---
title: "How to get Realtek RLT8185 working with ndiswrapper?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Adamantus on 2009-01-17
Hey,

I'm actually using Linux Mint, but their forums are so slow that it is almost impossible to get a questions answered. Anyway, I've been looking around google and lots of forums but nowhere are there good, clear directions about how to get ndiswrapper working. Everything has been very complicated, and I'm too new to Linux to understand most of it. Does anyone know how (or have a link) to get ndiswrapper working with a Realtek RLT8185 wireless chipset?

---

### Post by alan34 on 2009-01-18
Check that you have ndiswrapper and ndisgtk installed in Synaptic Package Manager.

Copy the XP .inf and .sys files to a new folder on your desktop from the wireless card windows install cdrom.


If you have installed ndisgtk you should have Windows Wireless Drivers as a menu item under System - Administration.

If you want to use the terminal ........

1) cd towhereyourfilesare
2) sudo ndiswrapper -i yourfile.inf
3) sudo ndiswrapper -l                  (letter l)
4) sudo depmod -a
5) sudo modprobe ndiswrapper
6) sudo ndiswrapper -m
7) gksudo gedit /etc/modules
8) gksudo gedit /etc/modprobe.d/blacklist

3) - should give you something like this

alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan:
net8185 : driver installed
device (10EC:8185) present
alan@alan-desktop:~$

7) is add **ndiswrapper** on a line on its own at the bottom of the file

and 8) is blacklisting the kernal module like so

[B]#Linux wireless driver
blacklist r8180
blacklist r818x	
[/B]

I have assume Linux Mint is Gnome but if not use

sudo nano to edit the files required.

I have this card and had to use ndiswrapper until Intrepid but now it works with the Linux drivers :-)

---

