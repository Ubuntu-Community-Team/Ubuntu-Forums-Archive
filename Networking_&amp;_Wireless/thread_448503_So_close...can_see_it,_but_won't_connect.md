---
title: "So close...can see it, but won't connect"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by bkinney on 2007-05-19
I just installed feisty and I have a Linksys wireless-g usb adapter.  When I click on the network connection icon on the top right I can see the wireless network (called "default") and I try to click to connect but nothing happens.  Any suggestions on what I am missing??

- bkinney

---

### Post by Psicolonia on 2007-05-19
sure, is it ad-hoc?? does it have a password? wep? what type? is it a rout? :)

just tell me more about the network and how many network cards you have ;)

---

### Post by pebo on 2007-05-19
If you're referring to the NetworkManager applet ("nm-applet") have you read /usr/share/doc/network-manager/README.Debian? It tells you > Only devices that are *not* listed in /etc/network/interfaces or which have 
been configured "auto" and "dhcp" (with no other options) are managed by NM.Edit the file in a terminal with ```
sudo nano /etc/network/interfaces
```and comment out all the interfaces **except** the section with loopback in by putting a # in front of each line. After modifying /etc/network/interfaces you have to restart NM with the command "sudo /etc/dbus-1/event.d/25NetworkManager restart"
HTH

---

### Post by prince sparkle on 2007-11-06
I Have an AD HOC network for internet access in my home. I'm a Linux newbie so I dont know much. however i have a similar problem, i have a multiple boot on my laptop (consisting of XP, Vista and Gusty) windows installations will connect to my network fine. ubuntu will see it and its name but it wont connect. I have no green orbs in the corner it just tries to connect then gives up. :confused: am I missing something???

..ps this is an open connection with no security.

---

