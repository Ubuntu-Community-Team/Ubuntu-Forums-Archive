---
title: "My wifi still not working, despite installing the drivers. Non working command."
date: 2011-08-14
forum: New to Ubuntu
---

### Post by MiNTsuid on 2011-08-14
Hey all.
 
My currently version of linux: Ubuntu 11.04 (x64). 
My wirelles card is: Atheros USB 2.0 Wireless adapter.
I installed ubuntu through wubi.
 
My ubuntu can't read my wifi card. I try install drivers from windows, therefore I installed ndiswrapper. I found tutorial which show me how to install ndiswrapper. 
 
It's this tutorial.
```
 
You can download .deb ndiswrapper packages here 
Alternatively, you can install the same using apt-get command:
 $ apt-cache search ndiswrapper-utils
 Output (note version number 1.9):
 ndiswrapper-utils-1.9 - Userspace utilities for the ndiswrapper linux kernel module 
Now install it:
 $ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
Step # 2: Copy .INF and .SYS files
 
You need to copy .INF and .SYS files from CD / floppy disk provided with your device. You can also obtain driver from manufactures web site.
 
Step # 3: Install Driver
 
To install driver, enter:
 $ sudo ndiswrapper -i driver-name.inf
 Verify that driver was installed:
 $ ndiswrapper -l 
Finally, install ndiswrapper driver
 $ sudo modprobe ndiswrapper

```
 
I've) downloaded and installed these packages and copied .inf and .sys files and installed drivers. But i don't know what's going on this:
 
```
 
$ sudo modprobe ndiswrapper

```
 
I wrote this command in terminal, but nothing happens.
what am I doing wrong? I install drivers, but my wireless further not work.
I have only packages folder for ndiswrapper.
 
What i should doing with .sys file?
 
If you can please write tutorial how to install ndiswrapper and install drivers from windows.
Remember: I'm only newbie.

---

### Post by HalfEmptyHero on 2011-08-14
Try doing running sudo update-initramfs after running modprobe ndiswrapper and then restart your computer. I can't guarantee it will work, as I don't use ndiswrapper, but it won't hurt to try.

---

