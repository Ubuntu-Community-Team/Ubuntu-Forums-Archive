---
title: "Help install .BIN program"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by sqrooup on 2009-02-25
As part of ongoing studies for CCNA certification I have found and downloaded a copy of Packet Tracer for Ubuntu/Linux from the Cisco website. This tool came as a .BIN file. I have done this before, with Google Earth, but have forgotten the procedure; can anyone remind me how to do it?

Note; > *From the Cisco website FAQ:*
**Q. Why can&#8217;t I create a custom device in the Linux Ubuntu version of Packet Tracer?**
A. In order to create a custom device, the Packet Tracer application needs to be able to write to the PT/template folder. In Ubuntu, Packet Tracer must be installed at the root level, and then run as root to successfully write to this folder.
I will need to run it as root!

---

### Post by ktemkin on 2009-02-25
This is a raw binary installer- the closest thing you'll find on Ubuntu/Linux to an EXE file.

In order to run it as root, locate it in the terminal, and type:

sudo /path/to/file

If you're in the same directory as the file, you can type "sudo ./filename"; as "./" means "the current folder". You can't just type in the command by itself, as when a command isn't in the form of a location, Ubuntu checks for it in a few special places, known as the 'PATH'.

Sudo is the Super User Do command, which will (at least in most distributions) allow you to use your password to run commands as root. Note that you should exercise caution in doing so; you should only run commands you trust as root.

---

### Post by handydan918 on 2009-02-25
Two comments:
1) What's the problem? Install and run the program with sudo (gksudo if graphical).
2) Packet tracing utils are installed/available for Ubu. (Just open synaptic and search for traceroute.)

---

### Post by Michael.Godawski on 2009-02-25
You can use the terminal, so navigate into the directory in which the bin file is located - you can use the cd command to change directories:
```
chmod +x file.bin
./file.bin

```Sometimes a sudo has to be put in front of these commands.
The chmod command makes the bin file executable, sometimes this is needed too.

---

