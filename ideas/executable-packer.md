# Portfolio Website

|     Author     | Last Updated |        Time Estimate         |
| :------------: | :----------: | :--------------------------: |
| Michael Vaughan |  07/29/2022  | Short - 🟩🟩🟩⬜️⬜️ - Long |

## Description

*This project can vary widely depending on implementation details.*

An executable packer takes an executable, and obfuscates it on disk. The idea is to prevent easy reverse engineering. It is often performed by malware and by proprietary software of old, before SaaS.

Packers can be written for both PE files on Windows or ELF or Mach-O binaries on Linux and MacOS, respectively. Implementation details differ, but most packers will take an arbitrary binary and pack it. The end result, a packed executable, has two components: The payload and the stub.

The payload is packed in some way - compressed, encrypted, split, maybe all three or more. This packed payload is loaded by the stub, a program that undoes the packing process and executes the payload. An example is when the payload is appended to the end of a stub, that reads itself into memory, seeks to the payload, unpacks it, and drops it to disk before executing.

In practice there is no such thing as a perfect packer - the code can always be reverse engineered if it is running on your own machine - but there are many ways to slow down the reverse engineering process.

## Goals

- [ ] Execute an arbitrary binary from somewhere - over the network, as a resource, or just read in from the end of the current file
- [ ] Add obfuscation/compression/encryption of the payload

## Going Further

- Manual mapping. Programs are loaded from the kernel, but they do not need to be. Many packers will perform the loading of memory segments, relocations, etc all on their own for additional obfuscation
- Process Injection. Other packers will inject the payload into a foreign process on the machine.
- Anti-debugging & anti-VM routines
- Automatically packed builds of other projects
    - CD pipeline
