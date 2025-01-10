# Minigrep

Minigrep is a simplified implementation of the classic command-line search utility `grep` (Global Regular Expression Print), written in Rust. This tool allows you to search for specific text patterns within files, demonstrating core Rust concepts like error handling, file I/O, and environment variables.

## Features

- Case-sensitive text search within files
- Optional case-insensitive search using environment variable
- Clear error messaging for invalid inputs
- Command-line interface with argument parsing

## Installation

1. Ensure you have Rust and Cargo installed on your system. If not, install them from [rustup.rs](https://rustup.rs)
2. Clone this repository:
   ```bash
   git clone [your-repository-url]
   cd minigrep
   ```
3. Build the project:
   ```bash
   cargo build --release
   ```

## Usage

Basic usage pattern:
```bash
minigrep <search_query> <file_path>
```

Example:
```bash
minigrep "pattern" poem.txt
```

### Case Insensitive Search

To perform a case-insensitive search, set the `IGNORE_CASE` environment variable:

```bash
# On Unix/Linux/macOS
IGNORE_CASE=1 minigrep "pattern" poem.txt

# On Windows PowerShell
$env:IGNORE_CASE=1; minigrep "pattern" poem.txt
```

## Project Structure

- `main.rs`: Entry point of the application, handles command-line argument parsing and program execution
- `lib.rs`: Core functionality including:
  - `Config`: Structure for storing program configuration
  - `run`: Main program logic
  - `search`: Case-sensitive search implementation
  - `search_case_insensitive`: Case-insensitive search implementation

## Error Handling

The program includes robust error handling for common scenarios:
- Insufficient command-line arguments
- File reading errors
- Invalid UTF-8 text content

Error messages are written to stderr using `eprintln!` to maintain proper separation of program output and error messages.

## Testing

The project includes unit tests demonstrating the core functionality. Run the tests using:

```bash
cargo test
```

Tests cover both case-sensitive and case-insensitive search functionality.

## Technical Details

### Search Implementation

The search functionality is implemented in two variants:
1. Case-sensitive search (`search` function)
2. Case-insensitive search (`search_case_insensitive` function)

Both implementations use Rust's iterator methods and string manipulation, demonstrating idiomatic Rust code.

### Memory Management

The program uses Rust's ownership system to ensure memory safety:
- String slices (`&str`) are used for efficient text searching
- The `'a` lifetime parameter ensures proper reference handling
- Cloning is minimized to maintain performance

## Contributing

Feel free to submit issues and enhancement requests. Follow these steps to contribute:

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## Acknowledgments

This project is inspired by the Rust Programming Language Book's command-line project tutorial.
