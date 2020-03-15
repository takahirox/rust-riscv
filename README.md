# riscv-rust

riscv-rust is a [RISC-V](https://riscv.org/) processor emulator project written in Rust.

## Demo

[Online demo with xv6](https://takahirox.github.io/riscv-rust/index.html)

[xv6-riscv](https://github.com/mit-pdos/xv6-riscv) is the RISC-V port of xv6 which is UNIX V6 rewritten by MIT in the current C language for x86.

## Features

- Emulate RISC-V processor and peripheral devices
- Stable as [xv6-riscv](https://github.com/mit-pdos/xv6-riscv) runs on it
- Runnable locally
- Also runnable on browser with WebAssembly

## Screenshots

![standalone](./screenshots/standalone.png)

![WASM](./screenshots/wasm.png)

## Instructions/Features support status

- [x] RV32/64I
- [x] RV32/64M
- [ ] RV32/64F
- [ ] RV32/64D
- [ ] RV32/64Q
- [ ] RV32/64A
- [ ] RV32/64C
- [ ] RV32/64Zifencei
- [ ] RV32/64Zixsr
- [ ] CSR
- [x] SV32
- [x] SV39
- [ ] SV48
- [ ] Privileged instructions

etc...

## How to build riscv-rust and run xv6

### Standalone

```sh
$ git clone https://github.com/takahirox/riscv-rust.git
$ cd riscv-rust
$ cargo run --release xv6/kernel -f xv6/fs.img
```

### WebAssembly

Prerequirements
- Install [wasm-bindgen client](https://rustwasm.github.io/docs/wasm-bindgen/)

```sh
$ git clone https://github.com/takahirox/riscv-rust.git
$ cd riscv-rust
$ cargo build --release --lib --target wasm32-unknown-unknown
$ wasm-bindgen ./target/wasm32-unknown-unknown/release/riscv_rust.wasm --out-dir ./wasm/ --target web --no-typescript
# boot local server and access index.html
```

## How to build and run riscv-tests

Prerequirements
- Install [riscv-gnu-toolchain](https://github.com/riscv/riscv-gnu-toolchain)
- Install [riscv-tests](https://github.com/riscv/riscv-tests)

```sh
$ git clone https://github.com/takahirox/riscv-rust.git
$ cd riscv-rust
$ vi build_tests.sh # edit the path to the installed riscv-tests
$ bash build_test.sh
$ cargo run ./tests/rv32ui-p-add
```
