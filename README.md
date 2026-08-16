"""
Task-01: Implement Caesar Cipher
---------------------------------
A Python program that encrypts and decrypts text using the Caesar Cipher
algorithm. The user provides a message, a shift value, and chooses whether
to encrypt or decrypt.
"""


def caesar_encrypt(text: str, shift: int) -> str:
    """Encrypt text using the Caesar Cipher with the given shift."""
    result = []
    for char in text:
        if char.isupper():
            shifted = (ord(char) - ord('A') + shift) % 26
            result.append(chr(shifted + ord('A')))
        elif char.islower():
            shifted = (ord(char) - ord('a') + shift) % 26
            result.append(chr(shifted + ord('a')))
        else:
            # Leave digits, spaces, punctuation, etc. unchanged
            result.append(char)
    return ''.join(result)


def caesar_decrypt(text: str, shift: int) -> str:
    """Decrypt text using the Caesar Cipher with the given shift."""
    return caesar_encrypt(text, -shift)


def get_shift_value() -> int:
    """Prompt the user for a valid integer shift value."""
    while True:
        try:
            return int(input("Enter shift value (integer): ").strip())
        except ValueError:
            print("Invalid input. Please enter a whole number (e.g. 3).")


def main():
    print("=" * 50)
    print("        CAESAR CIPHER — ENCRYPT / DECRYPT")
    print("=" * 50)

    while True:
        print("\nChoose an option:")
        print("  1. Encrypt a message")
        print("  2. Decrypt a message")
        print("  3. Exit")
        choice = input("Enter choice (1/2/3): ").strip()

        if choice == '1':
            message = input("Enter the message to encrypt: ")
            shift = get_shift_value()
            encrypted = caesar_encrypt(message, shift)
            print(f"\nOriginal Message : {message}")
            print(f"Shift Value      : {shift}")
            print(f"Encrypted Message: {encrypted}")

        elif choice == '2':
            message = input("Enter the message to decrypt: ")
            shift = get_shift_value()
            decrypted = caesar_decrypt(message, shift)
            print(f"\nEncrypted Message: {message}")
            print(f"Shift Value      : {shift}")
            print(f"Decrypted Message: {decrypted}")

        elif choice == '3':
            print("Exiting program. Goodbye!")
            break

        else:
            print("Invalid choice. Please enter 1, 2, or 3.")


if __name__ == "__main__":
    main()
