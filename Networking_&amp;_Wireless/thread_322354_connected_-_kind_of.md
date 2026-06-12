---
title: "connected - kind of"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by benndamann33 on 2006-12-20
I am connected to wireless and wired networks but can't use my internet. No idea how this happened. Tried to install network-manager-gnome and did so successfully, followed steps aobut going and editing /etc/networking/interfaces file and commenting out everything except for lo connection.  Firstly, I can't access the gnome network manager, it's installed but can't find it anywhere on my computer. Seconldy, by going to setting - admin - networking it shows all of my devices as unconfigured. I tried uncommenting these lines and doing ifconfig, ifdown, ifup. No luck. I'm connected but if I go to an internet browser gives me no connection pages. Totally useless laptop now, I'd really appreciate any help. I'm using dapper and a d610 laptop. 
Ben

---

### Post by Iowan on 2006-12-20
You'll need to uncomment those interfaces you have (as you've reported doing).  You might post your **/etc/network/interfaces** file and the results of **ifconfig**. I'm more familiar w/ wired connections (but certainly no expert) - is your machine a static IP address or is it supposed to get an address via DHCP?  Although a bit late now... I tend to make a backup copy of configuration files before editing them.  Besides providing a baseline (for disaster prevention), it lets me keep a copy of the comments, but streamline the "working" file.

---

### Post by usererror on 2006-12-20
Ben,

I also just got done struggling to get NetworkManager to work aka network-manager-gnome in package manager. i got it installed and then went to Networking under System and unchecked all the "Enable this device".

Then from the command prompt restarted networkint (/etc/init.d/networking restart) after that ran "NetworkManager" case sensative from the command line and I got a new icon up by the clock.  

hopefully that works for you!

---

