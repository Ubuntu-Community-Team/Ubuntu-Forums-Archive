---
title: "Installing Peng On Kubuntu"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by LongH on 2009-03-23
I was trying to install Peng AOL on kubuntu so that I can access my AOL dial-up account. I tried to follow instructions from a website but I could not get is to work. Below are the commands I typed in and the error message I got out. Can anybody tell me what I am doing wrong?

hunter@Blue:~/Desktop$ tar xzf peng1.05.tar.gz
hunter@Blue:~/Desktop$ cd peng
hunter@Blue:~/Desktop/peng$ ./recompile
loading cache ./config.cache
checking host system type... i386-pc-none
checking target system type... i386-pc-none
checking build system type... i386-pc-none
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for a C-Compiler...
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
Making clean in .
make[1]: Entering directory `/home/hunter/Desktop/peng'
make[1]: Nothing to be done for `clean-am'.
make[1]: Leaving directory `/home/hunter/Desktop/peng'
Making clean in peng
make[1]: Entering directory `/home/hunter/Desktop/peng/peng'
test -z "peng" || rm -f peng
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
make[1]: Leaving directory `/home/hunter/Desktop/peng/peng'
Peng lite 1.0.5
---------------

Assuming language: en_US.UTF-8

In this version you can conditinal compilation making
(May not compile all drivers that you don't need)

Do you want to actived this option ?
answer by (y or n)
n
Standart compilation











Please wait while Peng lite 1.0.5 is compiling -> make.log

Peng's commands (log you as root to use peng)

-a --adduser [login] [password]
-c --connect [login]
-d --deluser [login]
-i --listdriver
-k --kill
-l --listuser
-m --makeinit
-r --restore
-s --still
-v --version
-x --log


Configuration files location: /etc/PengAol/
Compilation Error, please consult: make.log
hunter@Blue:~/Desktop/peng$

---

### Post by Bachstelze on 2009-03-23
You need to install the compilation toolchain:

```
sudo apt-get install build-essential
```

---

### Post by LongH on 2009-03-24
Thank you very much! Now that I know what is wrong, is there any way to install the compilation toochain on the computer without an internet connection? I have a laptop running windows which could be used to download any files that are needed.

---

