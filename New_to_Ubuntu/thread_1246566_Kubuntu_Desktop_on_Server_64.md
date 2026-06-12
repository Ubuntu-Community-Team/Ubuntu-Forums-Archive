---
title: "Kubuntu Desktop on Server 64"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by rajathegoof on 2009-08-21
Hi,

If I do sudo apt-get install kubuntu-desktop, will it automatically download 64 bit? I currently have 64 bit server installed...or do I have to install different package?

Thanks in advance

.raja

---

### Post by starcraft.man on 2009-08-21
The apt backend handles all of that. Yes, there are separate packages for 64 bit, and if thats what your running, it will be installed. The odd package not in main repos supported by ubuntu might only have 32, they usually run decently without tweaking.

Might be a bit of a big download, just fyi. I assume your on a stripped down server, lots of packages to install.

---

### Post by rajathegoof on 2009-08-21
[starcraft.man]("http://ubuntuforums.org/member.php?u=250927"),

Thanks...yes the current machine does have minimal install, lamp and ssh and that's pretty much it. Hopefully that Verizon 20MB download will help, I am consistently getting 16-18MB.

I am converting this machine as desktop for my day to day usage like email/word processing and GIMP. To be frank, I am coming back to Linux world after long absence and trying to see if it is ready for Desktop replacement. So I am fairly new to Ubuntu/Kubuntu world. I currently use Windoz and Solaris. 

If I may ask another question,

I am building a new PC (in fact all the parts just arrived today), it will be used mainly as workstation, I run heavy server applications (Oracle DB and WebLogic), and plan to run VM (most likely via KVM or VirtualBox) with Win XP guest for applications that I cannot replace and only runs on XP. Is it wise to install server 64 first and then install Kubuntu-desktop or simply install Kubuntu Desktop 64? 

The spec for the machine below

Antec 300 Case
Crossair 1333 12GB DDR3
i7 920
Crosair 750w PSU
EVGA nVidea 9800 512MB DUAL DVI
Currently Segate Barracuda 1.5 TB, plan to run SSD for booting and use fakeraid 10 for data later
2 NIC
ASUS P6T MB
Two Dell 19 inch monitor

If I can get this to running Kubuntu for majority of my Work and Desktop stuf,, I can skip Windows 7 :-)

Thanks again for your help.

.raja

---

### Post by starcraft.man on 2009-08-21
> **rajathegoof said:**
> [starcraft.man]("http://ubuntuforums.org/member.php?u=250927"),

Thanks...yes the current machine does have minimal install, lamp and ssh and that's pretty much it. Hopefully that Verizon 20MB download will help, I am consistently getting 16-18MB.

I am converting this machine as desktop for my day to day usage like email/word processing and GIMP. To be frank, I am coming back to Linux world after long absence and trying to see if it is ready for Desktop replacement. So I am fairly new to Ubuntu/Kubuntu world. I currently use Windoz and Solaris. 

If I may ask another question,

I am building a new PC (in fact all the parts just arrived today), it will be used mainly as workstation, I run heavy server applications (Oracle DB and WebLogic), and plan to run VM (most likely via KVM or VirtualBox) with Win XP guest for applications that I cannot replace and only runs on XP. Is it wise to install server 64 first and then install Kubuntu-desktop or simply install Kubuntu Desktop 64? 

Completely, irrelevant. It's pretty much the same thing downloading and installing from the live CD, as installing from a server install and putting in the kubuntu-desktop package. Only difference, is large amount of bandwidth and time wasted on a server install. Why I always carry around a desktop and alt cd of my distros...
> 
The spec for the machine below

Antec 300 Case
Crossair 1333 12GB DDR3
i7 920
Crosair 750w PSU
EVGA nVidea 9800 512MB DUAL DVI
Currently Segate Barracuda 1.5 TB, plan to run SSD for booting and use fakeraid 10 for data later
2 NIC
ASUS P6T MB
Two Dell 19 inch monitor

If I can get this to running Kubuntu for majority of my Work and Desktop stuf,, I can skip Windows 7 :-)

Thanks again for your help.

.raja

You sir, have too much money. Give some to me rather than spending it on 12 GB of DDR3. That's insane.... also, it goes to a good cause. All these squirrels taking over need some food...

---

### Post by jacksaff on 2009-08-21
You get more control over the packages if you do a server install. You want as little as possible installed on a server to reduce any security vulnerabilities and to make upgrades as hassle free as possible. (apt makes them pretty hassle-free already).

You might want to do something like have a gui-free base install and then install kubuntu into a virtual machine. 

All of your virtual machines in fact would run on the non-gui base install which will give security and maintenance benefits.

It would also let you muck around with a kubuntu system (or two or ...) and if you trash it, your base install and all the other vms will be unaffected.

---

