---
title: "Wifi help needed"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by Dark Figure on 2008-08-29
Ok, I have spent a few days trying to do this entirely on my own, with the help of some posts made on the topic on this message board.

However, I have gotten to the point were I needed to register and try to enlist some customized help.

Regarding Linux / Ubuntu I am about a 0.5 out of 10 on knowledge. XP, and general computer know how I'd rate myself at a 8/10. My problem is obviously with getting the wifi working on my Laptop. So here is some information that I think would be helpful to know. Everything works fine, just not the wifi.

I do not have the required knowledge to really troubleshoot and play around. I have installed Ubuntu using the WUBI option.



Laptop Info:
Brand: Medion SIM2000/MD95021 (appears to be a re branded MSI-250) Pentium 4 1.4 ghz, 512 megs of ram, 60 gig HD.


Wifi Info: 
Card: Intersil Corp ISL 3886 [Prism Javelin/Prism Xbow] Rev01
PCI Address 00:0e.00280:
1260:3886

Windows XP Wifi Drivers:
PRISMAOO.inf
PRISMAOO.sys

I have loaded these using the GUI version of ndiswrapper. However I have been told that the hardware is not present.

At this point, I have removed ndiswrapper with the synaptic package manager.

I figure I will wait before trying anything further.

So, any help (I know this must be getting tiresome for you guys) would be much appreciated.

I do have a couple posts bookmarked but as I said, I feel like I really need some hands on, help from what I understand I have one of the "shitty" wifi cards lol

I really want to have a complete Ubuntu setup, I tried it on my desktop and it worked right out of the box, wifi and all. I wish my laptop was as friendly.

---

### Post by cmat on 2008-08-29
Have you tried a driver installation using the command line ndiswrapper? I found the GUI complicated things more than it should.

---

### Post by Dark Figure on 2008-08-29
I have been using jfinkels post as a guide @ [http://ubuntuforums.org/showthread.php?t=692218&page=3](http://ubuntuforums.org/showthread.php?t=692218&page=3)

Perhaps if I can go step by step with this, through this post with the assistance of the experts I can work to getting this thing working.


Ok, I used the code:

"sudo aptitude install ndiswrapper" in the terminal (I first uninstalled the previous GUI ndiswrapper package, and placed my Ubuntu cd in the drive)



I received the following.



administrator@administrator-laptop:~$ sudo aptitude install ndiswrapper 
[sudo] password for administrator:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Reading extended state information       
Initializing package states... Done 
Writing extended state information... Done 
Building tag database... Done              
Couldn't find package "ndiswrapper".  However, the following 
packages contain "ndiswrapper" in their name: 
  ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9  
Couldn't find package "ndiswrapper".  However, the following 
packages contain "ndiswrapper" in their name: 
  ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9  
No packages will be installed, upgraded, or removed. 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 0B will be used. 
Writing extended state information... Done 
Reading package lists... Done              
Building dependency tree        
Reading state information... Done 
Reading extended state information       
Initializing package states... Done 
Building tag database... Done       
administrator@administrator-laptop:~$  

I am not entirely sure that that process was a success, did I miss something?



Next I did this in the terminal

"sudo ndiswrapper -i PRISMAOO.inf" 

It gave me this message "sudo: ndiswrapper: command not found"

I am figuring something was not correctly loaded, perhaps I should use the synaptics package manager to install ndiswrapper?

Also, I have my wifi XP drivers on a usb thumb drive.

---

### Post by cmat on 2008-08-29
search for ndiswrapper in synaptic. the application's name in the repo might have changed since that guide was made.

---

### Post by Crafty Kisses on 2008-08-29
Can I see the results of:
```
lshw -C network
```

---

### Post by Dark Figure on 2008-08-29
Awesome, I was not entirely sure I would get much of a response. I'd like to say thanks in advance, and I apologize for my slow responses. I am trying to respond thoroughly and since only my desktop is on the net, I have to go back and forth between desktop and laptop, with my usb drive to copy over information.




Cmat, I did a search and it is there. Should I install them ?

I'm going to take all this one step at a time so I wont mistakenly miss, or screw up any steps.

[IMG][IMG]http://i3.photobucket.com/albums/y95/tykel/ndis.jpg[/IMG][/IMG]



Codename, you asked to see the results of "lshw -C network" here they are below.


administrator@administrator-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0              
       description: Ethernet interface 
       product: SiS900 PCI Fast Ethernet 
       vendor: Silicon Integrated Systems [SiS] 
       physical id: 4 
       bus info: pci@0000:00:04.0 
       logical name: eth0 
       version: 90 
       serial: 00:11:09:7b:1c:e1 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes 
  *-network:1 UNCLAIMED 
       description: Network controller 
       product: ISL3886 [Prism Javelin/Prism Xbow] 
       vendor: Intersil Corporation 
       physical id: e 
       bus info: pci@0000:00:0e.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=64 maxlatency=28 mingnt=10 
administrator@administrator-laptop:~$

---

### Post by ApUUbunU on 2008-08-29
Dark Figure,

You might find [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") useful if you get stuck.

You did correctly for searching for ndiswrapper in the package manager. Instead, try typing "ndis", and you will see another package called "ndisgtk". Go ahead and click the boxes next to this package ( as well as "ndiswrapper-common" and "ndiswrapper-utils-1.9", and follow the following screens for downloading them. That should be fairly easy.

The next step is to download the windows drivers for your card.

This link:

[http://www.sis.com]("http://www.sis.com")

should contain the windows drivers.

Click on "Download" on that page, and in the first box choose "Windows XP". In the next box choose "Network Driver" and in the box after that, "SiS 900 & Integrated Sis Lan". Click on go and you will arrive at a page where you can download the driver. Go ahead and do that, and reply you progress.

EDIT: It is possible you do not need windows drivers. There is also a Linux driver for your card. Instead of clicking "Windows XP", choose "Linux" instead, and follow the rest of the instructions as given. However, I do not know if it is easy to install this driver, or otherwise.

---

### Post by Dark Figure on 2008-08-29
ApUUbunU,

I have downloaded the drivers (XP and Linux) I was not aware that there is a linux driver available.

I was not aware that SiS was the manufacturer of my Laptops wireless card. They are the video card, Ethernet and system boards chipsets however.

If this Linux driver is available by them I cant see why Ubuntu would not activate my wireless card even while running the live cd


I am going to wait for some more feed back before I try anything else. As I am not entirely sure those drivers are correct or needed. I copied the XP wifi drivers from my laptops recovery cd, and then verified the files with XP's device manager. If that SiS Linux driver is the correct one for my WiFi card then that would theoretically save me from having to use ndiswrapper. I'd just have to be told the instructions for making it all work.



Right now I have reinstalled ndiswrapper though, through the synaptic program manager. I'm going to wait this out and see what everyone else has to say about a course of action and the info I have posted.

I do appreciate this very much so. It saves me from having to aimless poke around not knowing whats wrong or right.



Cmat, 

I also did "sudo ndiswrapper -i PRISMAOO.inf" again and this time instead of recieving 
the "sudo: ndiswrapper: command not found" message I did earlier,I received this one.


administrator@administrator-laptop:~$ sudo ndiswrapper -i PRISMAOO.inf
couldn't open PRISMAOO.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
administrator@administrator-laptop:~$ 

After this I tried to copy PRISMAOO.inf and PRISMAOO.sys to /usr/sbin/ but was not allowed to to the directory being protected.

---

### Post by Dark Figure on 2008-08-30
Anyone still alive out there? :)

---

