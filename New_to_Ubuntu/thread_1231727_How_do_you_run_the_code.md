---
title: "How do you run the code?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by placebo202 on 2009-08-04
hi,
    
    How do you compile the code without using the terminal? I think my computer does not have the complier downloaded onto it when i installed ubuntu. there is no such program that allows me to compile and execute the code I've written on the computer somewhere else. Help please :D

---

### Post by llamabr on 2009-08-04
seems quicker to me to install the compiler software, but if you want to do it without the terminal, for whatever reason:

```
brock@hops:~$ apt-cache search gui compiler
ndoc-doc - Code documentation generator for .NET
swig - Generate scripting interfaces to C/C++ code
cmake-gui - GUI for cmake cross-platform make system
fwbuilder - Firewall administration tool GUI
fwbuilder-bsd - Firewall Builder policy compiler(s) for BSD based firewalls
fwbuilder-cisco - Firewall Builder policy compiler(s) for Cisco based firewalls
fwbuilder-common - Firewall administration tool GUI (common files)
fwbuilder-dbg - Firewall administration tool GUI (debugging symbols)
fwbuilder-doc - Firewall administration tool GUI documentation
fwbuilder-linux - Firewall Builder policy compiler(s) for Linux based firewalls
gambas2-dev - Gambas compilation tools
libb-size-perl - Measure size of Perl OPs and SVs
libwxsmithlib0 - wxSmith shared library (wxSmith is a Code::Blocks plugin for RAD GUI editing)
ocaml-core - OCaml core tools (metapackage)
swig1.3 - Generate scripting interfaces to C/C++ code
brock@hops:~$ 

```

---

### Post by doas777 on 2009-08-04
> **placebo202 said:**
> hi,
    
    How do you compile the code without using the terminal? I think my computer does not have the complier downloaded onto it when i installed ubuntu. there is no such program that allows me to compile and execute the code I've written on the computer somewhere else. Help please :D

if you want to compile but via a gui, then i recommend you find an IDE: [http://ubuntuforums.org/showthread.php?t=6762](http://ubuntuforums.org/showthread.php?t=6762)

are you posting for a psychology experiment? I notice your username.

---

