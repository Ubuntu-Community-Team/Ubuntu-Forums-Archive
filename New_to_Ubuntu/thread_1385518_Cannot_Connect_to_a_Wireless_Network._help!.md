---
title: "Cannot Connect to a Wireless Network. help!"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by smdawson on 2010-01-19
Hello,
I just very recently switch my OS from Vista to Ubuntu because I hated Vista. However, I don't know anything about Ubuntu and I cannot get it to recognize a wireless internet connection. Again, I'm not super computer familiar, so if anyone could help me please be liberal in the instructions. If you need any info from me just let me know and I'll get it back up here a.s.a.p. Thank you!

---

### Post by J V on 2010-01-19
Network icon: Its the little plug icon in the tray

Rightclick the network icon and enable wireless, click it and choose your network then type in the password.

If its not listed, good for you! more work for me (doh!)

Rightclick the network icon and select edit connections, then go to wireless, and manually add your network ID and password.

---

### Post by synapsys on 2010-01-19
A lot of wireless cards are recognized by default in Ubuntu. First things first, click the network manager icon (next to volume in upper right hand corner) and see if it gives you a list of available wireless networks.

---

### Post by cenzorrll on 2010-01-19
you probably don't have the necessary drivers installed for your wireless card.

open Administration>Hardware Drivers and it should find any proprietary drivers for you.  you'll probably need to be plugged into the internet to install these drivers initially

if nothing comes up, in a terminal type:

```
lspci
```

and it'll pop up with a bunch of scary stuff, but you're looking for a line something like this (this is at the bottom of the output when i input the command):

```
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

the Broadcom Corporation BCM4322 is my wireless card and the Realtek etc is my ethernet card.

post it and then we can try to find a solution (or driver) from there

---

### Post by dertdamb on 2010-01-19
You shouldn't even need to use the terminal. Just go to the driver tool under the system menu on your desktop. Just run that and allow Ubuntu to activate the proprietary driver on your computer.

---

### Post by smdawson on 2010-01-19
thanks for the fast responses guys. I don't get any networks listed after I enable wireless connections. I have tried to enter an address manually but it's not really working for me. I looked at Hardware Drivers and it shows no proprietary drivers in use. Then i typed "lspci" (what does that mean? out of curiosity) into a terminal and the end of the text is as follows (I'm typing it, since I'm using a different computer now for internet access):
 
...Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
...Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by Greenwidth on 2010-01-19
See this guide:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I have the same card, the easiest way is to connect wired, but the drivers are also on the LiveCD.

---

### Post by smdawson on 2010-01-19
Is the LiveCD considered what you can have sent to you by Canonical (or whoever ), or will the CD I burned the ISO file to work?

---

### Post by 3rdalbum on 2010-01-19
> **smdawson said:**
> ...or will the CD I burned the ISO file to work?

Yes, they are the same thing really.

---

### Post by smdawson on 2010-01-19
Awesome! Thank you Greenwidth, and all others. I am now able to recognize wireless connections. My problem is officially solved.

---

### Post by smdawson on 2010-01-19
I'm not sure if this is proper etiquette, but you guys want to help me with another question? I was wondering (1) if I need anti-virus protection with Ubuntu, and (2) if I have to find Linux specific programs to run on Ubuntu? (i.e. I need to find a C++ IDE for Linux) Will Dev C++ work on Ubuntu, or does anyone have another good suggestions?

---

### Post by Miljet on 2010-01-19
You probably need to start a new thread for the new questions. Most people will only read as far as the first problem solved.

There is much discussion about anti-virus on Linux. The general consensus is that you do not need any anti-virus programs. All anti-virus programs only scan for Windows virus anyway. the only reason for using one would be to catch any malware before you forward it to your friends who are still using Windows.

Almost all of the programs that you will need are located in the ubuntu repositories. Just click on System -> Administration -> Synaptic Package Manager. Enter a search for the type programs you want or you can just browse through the thousands of programs available. When you find something you like, click on it, mark it for installation, and then click on apply at the top of the window. The program (or programs) will be automatically downloaded and installed for you. And by the way, all programs are also updated through a single source too. No more going to different sites to see if your installed software is up to date.

---

### Post by hero1900 on 2010-01-19
WELCOME TO UBUNTU
actually for now you don't need any anti virus (no viruses in ubuntu) for c++ there is many IDE that you can chose from look in ubuntu software center and type c++ you can use QT libraries for GUI since Linux different than windows but if it is the general libraries for c++ then no problem and you can even write the code in gedit (you can found in accessories) and then use gcc to compile and run (run in terminal man gcc to see how to use it) 
you can refer to this topic [http://ubuntuforums.org/showthread.php?t=1577](http://ubuntuforums.org/showthread.php?t=1577)
good luck and enjoy ubuntu is really good and full of knowledge

---

### Post by synapsys on 2010-01-20
> **smdawson said:**
> I need to find a C++ IDE for Linux

Code::Blocks

---

