# Basic-cistercian-number-encryption
basic cistercian number encryption using cistercian symbols

//

#include <iostream>
#include <unordered_map>
#include <string>

std::unordered_map<int, std::string> symbols = {
    {0, " "},
    {1, "╵"},
    {2, "╶"},
    {3, "└"},
    {4, "╷"},
    {5, "│"},
    {6, "┌"},
    {7, "├"},
    {8, "╴"},
    {9, "─"},
    {10, "┘"},
    {11, "┴"},
    {12, "╯"},
    {13, "┐"},
    {14, "┬"},
    {15, "┤"},
    {16, "╮"},
    {17, "┼"}
};

std::string encrypt(int number) {
    std::string result;
    while (number > 0) {
        int digit = number % 10;
        result = symbols[digit] + result;
        number /= 10;
    }
    return result;
}

int decrypt(const std::string& ciphertext) {
    int result = 0;
    for (char symbol : ciphertext) {
        for (const auto& pair : symbols) {
            if (pair.second == std::string(1, symbol)) {
                result = result * 10 + pair.first;
                break;
            }
        }
    }
    return result;
}

int main() {
    int number = 12345;
    std::string ciphertext = encrypt(number);
    std::cout << "Encrypted: " << ciphertext << std::endl;

    int decrypted = decrypt(ciphertext);
    std::cout << "Decrypted: " << decrypted << std::endl;

    return 0;
}
