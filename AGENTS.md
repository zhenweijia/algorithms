# alogrithms

算法练习，题目来源是各种OJ (algorithm/data-structure practice; problems from various Online Judges: LeetCode, PAT, HDU, etc.).

## Cursor Cloud specific instructions

### What this repo is
A flat collection of ~130 standalone C++ solution files (`*.cpp`) plus a few shared headers (`*.h`) at the repo root, with one extra file under `dynamic_programing/`. There is **no product, service, package manager, lockfile, or committed build system** — `CMakeLists.txt`, `main.cpp`, `bin/`, `obj/`, and `cmake-build-debug/` are all `.gitignore`d (the author used CLion locally). Each file is compiled and run individually.

### Toolchain
The base VM image already provides everything needed: `g++` 13.x (`build-essential`), `make`, and `cmake`. No dependencies need installing for normal work.

### Build & run a single solution
Compile file-by-file and run the produced binary (write binaries into `bin/`, which is gitignored):

```
g++ -std=c++11 -Wall some_file.cpp -o bin/some_file
./bin/some_file
```

Most files that have their own `int main()` read from **stdin** and write to **stdout** (OJ style), e.g. `echo 27 | ./bin/callatz`. Files that only contain a function/class (e.g. `two_sum.cpp`, `quickSort.cpp`) have no `main()` and are meant to be included/tested from a driver, not linked directly.

### Non-obvious gotchas
- There is no lint/test/build target and no CI. "Testing" a solution means compiling it and feeding it sample input.
- A handful of individual files do **not** compile as-is; these are pre-existing per-file source issues, not environment problems (do not "fix" them unless asked). Examples: `farmer_arcoss_river.cpp` (`#define and &&` clashes with the C++ `and` operator keyword — compile with `-fno-operator-names` if you must), `write_number.cpp` (missing `;`), `print_hex.cpp` (needs Boost headers: `sudo apt-get install -y libboost-dev`).
- Some solutions use GCC/`iso646.h`-style macros; prefer `g++` over `clang++` and keep `-std=c++11` (a few also work with `-std=gnu++11`).
