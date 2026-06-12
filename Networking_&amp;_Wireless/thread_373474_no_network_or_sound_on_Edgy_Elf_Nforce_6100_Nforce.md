---
title: "no network or sound on Edgy Elf Nforce 6100 Nforce 430 nvidia"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by marc66thomas on 2007-03-01
Hello folks 
I'm new to Ubuntu and hope to make it my new OS for this new box. 
I have tried dapper drake CD and it would not load, Edgy elf loads and installs on the hard drive Nice! 

I don't have Ethernet or sound for my Gigabyte S series GA-M61PM-S2 motherboard. This board has the new chip combo of northbrige and southbridge (NVIDIA GeForce 6150 SE GPU and NVIDIA nForce 430 MCP) integrated graphics Ethernet sata and raid. (Vista wouldn't load Ethernet either with out a new driver for the board) this makes me think that the nvidia chipset is too new to have a Linux driver. Running x86 install. 

1. So I have a real nubie question. which driver from the nvidia site is going to make this board sing with Edgy Elf?
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
do I want 
A.) Linux IA32 
B.) FreeBSD x86
C.) none of the above.

Thanks in advance.

---

### Post by Kobalt on 2007-03-01
I would advice two things : 
1. Please : Edgy Eft, and not Elf :)
2. Pick Linux IA32 
:rolleyes:

---

### Post by MBantz on 2007-03-05
Hi all,

ah!, my first posting :) Hurraa!

Well, I have exactly the same problem as Marc66thomas - but with 27 computers I just purchased for my work... swell, all with nForce 430 MCP chipset. All seems fine in Kubuntu (just getting the first PC up and running) - but no sound (driver included with CD - haven't tried it yet) and no ethernet. I put in an old 3Com nic, and the network is up and running - but I don't want to buy another 26 cards :( . The board(s) are Asus M2N DH. This board has no onboard GPU btw.

The page in question:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
is a link to graphics drivers, no good - didn't notice at first, and now my OpenGL is funny (i.e. nonexistent - but I expect to reinstall) or try Alberto Milone's superb Envy system,

the link 

[http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)

seems more interesting - but the zip contains only rpm's for other distros than kubuntu.

I will try to convert the rpm's (there are a bunch) to deb package with the alien -i command tomorrow - but if someone in this forum knows a workaround - please let us know :-)

On this forum I have seen postings about the older NFORCE-Linux-x86-1.0-0310-pkg1.run driver, but I get a compilation error running this script. (compiled my first kernel 10 years ago, and just returned to Linux a month ago - a bit rusty - and newbie I am..),

cheers,
Martin

---

### Post by MBantz on 2007-03-19
second posting yahee!

Well, just want to let you know, that the Asus motherboard, AMD64 dual core with nVidia 430MCP chipset is not easy to configure, without the right distribution,

I tried the newest distributions from Suse (the free version), Suse enterprise (booted from the CD but it couldn't find the CD-drive when installing), Fedora, Kubuntu (can't compile anything properly, X11 configuration is pretty manual), Feisty (couldn't install the live os),

the best distribution was Fedora, where only the on-board wireless didn't work,

but then enters PCLinuxOS2007, and voilá, everything works with a absolut minimum of fiddling,

just had to install nvidia drivers manually - took only 5 min., the wireless nic (realtek) was recognized, but with very low bandwidth - so I got a Linksys PCI wireless card and this works great - only needed to run the wireless wizard,

I can only recommend trying the Live CD and see what gets recognized, I've spent days googling around and was 1% from installing XP - but the system is far more complete and has a nice feeling to it than any other system I've tried,

I'll install this distribution on our 27 new computers for our learning center for kids and young people,


Cheers

---

### Post by Rotaj on 2007-03-30
I have a similar motherboard with the same video GPU. I am runnung Edgy with no problems regarding the audio or network connectivity. Have you tried the install from the AMD64 disk image (ISO)?

---

