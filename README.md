# pdfwordcount

Extremely basic shell wrapper around `pdftotext` and `wc` to get an approximate word count for a PDF file.

## Installation

### With Homebrew (macOS)

Use the [Homebrew](https://brew.sh/) package manager to install in one line:

```bash
brew tap sbibauw/utils
brew install pdfwordcount
```

### Manual installation

Install required dependency:

- `pdftotext`, available from [xpdf](https://www.xpdfreader.com/)

Clone the repo and copy the binary file to `/usr/local/bin`:

```bash
git clone https://github.com/sbibauw/pdfwordcount.git
cd pdfwordcount
chmod +x pdfwordcount
cp pdfwordcount /usr/local/bin/pdfwordcount
```

## Usage

```bash
pdfwordcount File.pdf
```

## Count logic

`pdfwordcount`, based on `wc`, counts words as sequences of characters separated by spaces or punctuation.

It filters in only strings starting with a letter, in order to avoid inflating the count with for instance tables containing many numbers.

It handles text with special characters by transliterating these to ASCII (e.g., `é` → `e`) internally (via `iconv`) in order to count them appropriately.
