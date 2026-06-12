---
title: "Ubuntu Studio not recognizing my wireless USB adapter"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Mikaelo1 on 2010-12-17
I am very, very new to Linux. I installed Ubuntu Studio perfectly but I need network connection. I now that is disabled by nature because of reported problems with audio. I did the dvd browsing (only two files were able to install the others couldn't)and tried synapsis (this synapsis I couln't get it so nothing came out of it). I am trying that ubuntu studio can recognize my wireless USB adapter (Belkin) but nothing. Please help!

---

### Post by Mikaelo1 on 2010-12-18
I have the Play wireless USB adapter

---

### Post by cchhrriiss121212 on 2010-12-20
> I did the dvd browsing (only two files were able to install the others couldn't)
You just need to install them in the right order, all the required dependencies are there on the DVD image.

If you find this too hard, then just try using regular Ubuntu, it might save you some time.

---

### Post by Mikaelo1 on 2010-12-21
I don't seem to get them in this right order

---

### Post by cchhrriiss121212 on 2010-12-21
If you try to install one it will say something like:
"This package requires package X"

So then you just search for package X and install that. They are all there on the DVD.

You could also install network manager from the repositories if you have a wired connection handy. It is much easier.

---

### Post by Mikaelo1 on 2010-12-21
oh man! Now I get it 
 
yes, I am tracking each one right now

---

### Post by Mikaelo1 on 2010-12-21
ok I installed the files network manager but the adapter still off
what do I do next?

---

### Post by cchhrriiss121212 on 2010-12-21
First reboot. Do you see the network manager applet on the taskbar now?

---

### Post by Mikaelo1 on 2010-12-21
The closest I see the word net work is in taskbar/places/network and if I click on it I get Windows Network icon if click on that it says " unable to mount location - failed to retriveshare from server"
 
USB wireless adapter is not even turning a light on

---

### Post by Mikaelo1 on 2010-12-22
What do I do next?

---

### Post by cchhrriiss121212 on 2010-12-22
Try opening a terminal, then put lsusb and press enter, this should list your device number. If you post it here I can look up how to get it going.
If you don't have network manager on your taskbar, put nm-applet into a terminal.

---

### Post by Mikaelo1 on 2010-12-22
I typed  lsusb and this came up
 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 002: ID 050d:615a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
and then I typed nm -applet
 
nm: option requires an argument -- 't'
Usage: nm [option(s)] [file(s)]
 List symbols in [file(s)] (a.out by default).
 The options are:
  -a, --debug-syms       Display debugger-only symbols
  -A, --print-file-name  Print name of the input file before every symbol
  -B                     Same as --format=bsd
  -C, --demangle[=STYLE] Decode low-level symbol names into user-level names
                          The STYLE, if specified, can be `auto' (the default),
                          `gnu', `lucid', `arm', `hp', `edg', `gnu-v3', `java'
                          or `gnat'
      --no-demangle      Do not demangle low-level symbol names
  -D, --dynamic          Display dynamic symbols instead of normal symbols
      --defined-only     Display only defined symbols
  -e                     (ignored)
  -f, --format=FORMAT    Use the output format FORMAT.  FORMAT can be `bsd',
                           `sysv' or `posix'.  The default is `bsd'
  -g, --extern-only      Display only external symbols
  -l, --line-numbers     Use debugging information to find a filename and
                           line number for each symbol
  -n, --numeric-sort     Sort symbols numerically by address
  -o                     Same as -A
  -p, --no-sort          Do not sort the symbols
  -P, --portability      Same as --format=posix
  -r, --reverse-sort     Reverse the sense of the sort
      --plugin NAME      Load the specified plugin
  -S, --print-size       Print size of defined symbols
  -s, --print-armap      Include index for symbols from archive members
      --size-sort        Sort symbols by size
      --special-syms     Include special symbols in the output
      --synthetic        Display synthetic symbols as well
  -t, --radix=RADIX      Use RADIX for printing symbol values
      --target=BFDNAME   Specify the target object format as BFDNAME
  -u, --undefined-only   Display only undefined symbols
  -X 32_64               (ignored)
  @FILE                  Read options from FILE
  -h, --help             Display this information
  -V, --version          Display this program's version number
nm: supported targets: elf32-i386 a.out-i386-linux pei-i386 elf32-little elf32-big elf64-x86-64 pei-x86-64 elf64-l1om elf64-little elf64-big plugin srec symbolsrec verilog tekhex binary ihex trad-core

---

### Post by realzippy on 2010-12-22
He wanted you to type:

```
nm-applet
```

without a space;not:

nm -applet

---

### Post by Mikaelo1 on 2010-12-22
my bad here it is:
 
** (nm-applet:2078): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

---

### Post by cchhrriiss121212 on 2010-12-22
> ** (nm-applet:207:cool:: WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
I just went through this set up in a VM and I'm getting the same error as you are here. It is a known bug according to the studio dev list. 10.10 has been a pretty poor release for audio IMO, there is no low latency kernel available and I've seen other issues with jack not starting too.

I don't have a clue how to fix this nm-applet thing so I'd recommend trying out regular Ubuntu 10.04 (thats if you are not put off Ubuntu by all this nonsense). Anything you want from studio can be found in the regular Ubuntu, so you won't be missing anything. This is a good PPA for audio stuff:
[https://launchpad.net/~falk-t-j/+archive/lucid]("https://launchpad.net/%7Efalk-t-j/+archive/lucid")

---

### Post by Mikaelo1 on 2010-12-22
Thanks man !  I'll just install ubuntu 10.4

---

### Post by Mikaelo1 on 2010-12-22
I had to download lubuntu because my computer is a 686.  And now I get the same message
 
** (nm-applet:1756): WARNING **: <WARN> constructor(): Couldn't initialize the D-Bus manager.

---

### Post by cchhrriiss121212 on 2010-12-23
Lubuntu comes with a network manager so you don't need to follow these steps anymore. If you are having trouble please start a new thread as it is a separate issue.

---

