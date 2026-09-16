# Encryption & Decryption Project

A C++ application for batch encrypting and decrypting files using a sequential task management system.

## Project Overview

This project provides a command-line utility to encrypt or decrypt all files in a specified directory. It features:

- **Batch Processing**: Process multiple files in a directory recursively
- **Task Queue Management**: Efficient task queue for handling multiple files
- **File I/O Operations**: Secure file reading and writing
- **Encryption/Decryption Engine**: Core cryption functionality
- **Environment-based Configuration**: Uses `.env` file for encryption keys

## Project Structure

```
.
├── src/
│   └── app/
│       ├── main.cpp                          # Main entry point
│       ├── encryptDecrypt/
│       │   ├── Cryption.cpp                  # Encryption/decryption implementation
│       │   ├── Cryption.hpp                  # Cryption header
│       │   └── CryptionMain.cpp              # Cryption main executable
│       ├── file-handling/
│       │   ├── IO.cpp                        # File I/O operations
│       │   ├── IO.hpp                        # IO header
│       │   ├── ReadEnv.cpp                   # Environment variable reading
│       ├── processes/
│       │   ├── ProcessManagement.cpp         # Task queue management
│       │   ├── ProcessManagement.hpp         # ProcessManagement header
│       │   └── Task.hpp                      # Task structure definition
├── test/
│   └── test1.txt                             # Test file
├── Makefile                                  # Build configuration
├── .env                                      # Environment variables (encryption key)
├── cryption                                  # Cryption executable (compiled)
├── encrypt_decrypt                           # Main executable (compiled)
└── README.md                                 # This file
```

## Executables

The project builds two executables:

1. **`encrypt_decrypt`** - Main application for batch file encryption/decryption
   - Takes a directory path and action (encrypt/decrypt)
   - Recursively processes all files in the directory
   - Queues tasks and executes them using ProcessManagement

2. **`cryption`** - Standalone cryption utility
   - Focused encryption/decryption operations

## Building the Project

### Prerequisites

- GCC compiler with C++17 support
- Make

### Build Commands

Build both executables:
```bash
make
```

Or use the VS Code task:
```bash
Ctrl+Shift+B  # Runs the default build task
```

Clean compiled files:
```bash
make clean
```

## Usage

### Running the Main Application

```bash
./encrypt_decrypt
```

The application will prompt you for:
1. **Directory path**: The path to the directory containing files to encrypt/decrypt
2. **Action**: Either "encrypt" or "decrypt"

Example:
```
Enter the directory path: 
./test/
Enter the action (encrypt/decrypt): 
encrypt
```

### Running the Cryption Utility

```bash
./cryption
```

## How It Works

1. **User Input**: Takes directory path and action (encrypt/decrypt)
2. **Directory Traversal**: Recursively iterates through all files in the directory
3. **Task Creation**: Creates a Task object for each file with the specified action
4. **Task Queue**: Submits tasks to ProcessManagement's task queue
5. **Execution**: Processes tasks asynchronously from the queue
6. **File Operations**: Reads, encrypts/decrypts, and writes files using the IO class

## Key Components

### Cryption Module (`src/app/encryptDecrypt/`)
Handles the core encryption and decryption logic.

### File I/O Module (`src/app/file-handling/`)
- `IO`: Manages file stream operations
- `ReadEnv`: Reads environment variables (encryption key from `.env`)

### Process Management (`src/app/processes/`)
- `ProcessManagement`: Manages task queues for concurrent processing
- `Task`: Represents individual encryption/decryption tasks

## Configuration

The encryption key is stored in the `.env` file in the project root:
```
1234
```

Update this value to change the encryption key used by the application.

## Compilation Flags

The Makefile uses the following compiler flags:
- `-std=c++17`: C++17 standard
- `-g`: Debug information
- `-Wall`: Enable all warnings
- `-I.` and include paths: Header file directories

## Dependencies

- **Standard C++ Library**: File system operations, streams, memory management
- **C++17 Filesystem**: For directory traversal and file operations

## Notes

- All files in the target directory are processed recursively
- Encryption and decryption operations preserve file structure
- Task queue enables efficient batch processing
- Environment variables are read at runtime from `.env`

## Future Enhancements

Potential improvements:
- Configuration file support
- Parallel processing optimization
- Progress bar for batch operations
- Error recovery mechanisms
- Support for multiple encryption algorithms
- Logging system for audit trails



## Author

Tushar Patle
