---
title: "Getlibs isn't working"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Commander_Bob on 2010-02-27
I am trying to install the [AVR32 Toolchain]("http://www.atmel.com/dyn/products/tools_card_mcu.asp?tool_id=4118") but the packages are for 32bit computers not 64bit.

I was able to install the packages by forcing the architecture, and I got most of them working using getlibs. However one, avr32gdbproxy, won't work. When I run getlibs on it I get ```
libmpfr.so.1: ppu-sysroot
libgmp.so.3: ppu-sysroot
The following i386 packages will be installed:
ppu-sysroot
Continue [Y/n]? y
Downloading ...
Installing libraries ...
```
then trying to run it 
```
avr32gdbproxy: error while loading shared libraries: libmpfr.so.1: cannot open shared object file: No such file or directory

```
running getlibs again gives the exact same thing. I even tried downloading the 32bit version of ppu-sysroot and installing it, nothing.

BTW I am using Ubuntu 9.10, I just upgraded from 9.04 and I had this working on there.

Any ideas?

---

### Post by Seregwethrin on 2011-06-26
Same error here.

I'm trying to install Google Chrome's 32-bit dependencies on 64-bit Ubuntu. It says "Installing..."

I thought it installed all. Then I tried to install 32-bit Google Chrome deb with dpkg and got exactly the same dependency errors.

---

