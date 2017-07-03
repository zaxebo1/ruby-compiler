# Ruby Compiler

Ahead-of-time (AOT) Compiler designed for Ruby.

- Compiling your Ruby application into a single executable
- Rails and Native C extensions Fully Supported
- Open Source, MIT Licensed

## Development Status

|                       |                                                       Master CI                                                                                                       |                                                                    RAM Test                                                                                               |                                                             Black-box Test                                                                                                 |
|:---------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|      **Windows**      |  [![Status](https://ci.appveyor.com/api/projects/status/93i36eliiy6v3686/branch/master?svg=true)](https://ci.appveyor.com/project/pmq20/ruby-compiler/branch/master)  |  [![Status](https://ci.appveyor.com/api/projects/status/0tjl0mvnief8nyti/branch/master?svg=true)](https://ci.appveyor.com/project/pmq20/ruby-compiler-ram/branch/master)  |  [![Status](https://ci.appveyor.com/api/projects/status/pa5g32i9b0jilnk2/branch/master?svg=true)](https://ci.appveyor.com/project/pmq20/ruby-compiler-blbt/branch/master)  |
|       **macOS**       |  [![Status](https://travis-ci.org/pmq20/ruby-compiler.svg?branch=master)](https://travis-ci.org/pmq20/ruby-compiler)                                                  |  [![Status](https://travis-ci.org/pmq20/ruby-compiler-ram.svg?branch=master)](https://travis-ci.org/pmq20/ruby-compiler-ram)                                              |  [![Status](https://travis-ci.org/pmq20/ruby-compiler-blbt.svg?branch=master)](https://travis-ci.org/pmq20/ruby-compiler-blbt)                                             |
|       **Linux**       |  [![Status](https://travis-ci.org/pmq20/ruby-compiler.svg?branch=master)](https://travis-ci.org/pmq20/ruby-compiler)                                                  |  [![Status](https://travis-ci.org/pmq20/ruby-compiler-ram.svg?branch=master)](https://travis-ci.org/pmq20/ruby-compiler-ram)                                              |  [![Status](https://travis-ci.org/pmq20/ruby-compiler-blbt.svg?branch=master)](https://travis-ci.org/pmq20/ruby-compiler-blbt)                                             |

## Install

### Windows

First install the prerequisites:

* [SquashFS Tools 4.3](https://github.com/pmq20/squashfuse/files/691217/sqfs43-win32.zip)
* [Bison](http://gnuwin32.sourceforge.net/packages/bison.htm)
* [Visual Studio 2010](https://www.visualstudio.com/) or newer
* [Ruby 2.4.1](https://rubyinstaller.org/)

Then download the executable `rubyc.exe` and run it from the Visual Studio Command Prompt.

### macOS

First install the prerequisites:

* [SquashFS Tools 4.3](http://squashfs.sourceforge.net/): `brew install squashfs`
* [Xcode](https://developer.apple.com/xcode/download/)
  * You also need to install the `Command Line Tools` via Xcode. You can find
    this under the menu `Xcode -> Preferences -> Downloads`
  * This step will install `gcc` and the related toolchain containing `make`
* [Ruby 2.4.1](https://www.ruby-lang.org/)

Then,

    curl -L https://sourceforge.net/projects/ruby-compiler/files/v0.1.0/rubyc-darwin-x64/download > rubyc
    chmod +x rubyc
    ./rubyc

### Linux

First install the prerequisites:

* [SquashFS Tools 4.3](http://squashfs.sourceforge.net/)
* `gcc` or `clang`
* GNU Make
* [Ruby 2.4.1](https://www.ruby-lang.org/)

Then,

    curl -L https://sourceforge.net/projects/ruby-compiler/files/v0.1.0/rubyc-linux-x64/download > rubyc
    chmod +x rubyc
    ./rubyc

## Usage

If `ENTRANCE` was not provided, then a single Ruby interpreter executable will be produced.

    rubyc [OPTION]... [ENTRANCE]
      -r, --root=DIR                   The path to the root of the application
      -o, --output=FILE                The path of the output file
      -d, --tmpdir=DIR                 The directory for temporary files
      -c, --clean                      Cleans temporary files before compiling
          --make-args=ARGS             Extra arguments to be passed to make
          --nmake-args=ARGS            Extra arguments to be passed to nmake
          --debug                      Enable debug mode
      -v, --version                    Prints the version of rubyc and exit
          --ruby-version               Prints the version of the Ruby runtime and exit
          --ruby-api-version           Prints the version of the Ruby API and exit
      -h, --help                       Prints this help and exit
          --examples                   Prints usage examples

## Examples

### Producing a single Ruby interpreter executable

    rubyc
    ./a.out (or a.exe on Windows)

### Bootstrapping

    git clone --depth 1 https://github.com/pmq20/ruby-compiler
    cd ruby-compiler
    rubyc bin/rubyc
    ./a.out (or a.exe on Windows)

### Compiling a CLI tool

    git clone --depth 1 https://github.com/pmq20/node-compiler
    cd node-compiler
    rubyc bin/nodec
    ./a.out (or a.exe on Windows)

### Compiling a Rails application

    git clone --depth 1 https://github.com/ruby-china/homeland
    cd homeland
    rubyc bin/rails
    DATABASE_URL=... ./a.out server (or a.exe on Windows)

## See Also

- [Libsquash](https://github.com/pmq20/libsquash): portable, user-land SquashFS that can be easily linked and embedded within your application.
- [Libautoupdate](https://github.com/pmq20/libautoupdate): cross-platform C library to enable your application to auto-update itself in place.
