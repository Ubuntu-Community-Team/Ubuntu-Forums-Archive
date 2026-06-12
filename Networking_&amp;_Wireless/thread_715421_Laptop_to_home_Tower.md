---
title: "Laptop to home Tower"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by MrFlorindi on 2008-03-04
Hey everyone, first time poster here!:confused:

Anyways, lol, my dad just bought me a new HP wide screen laptop and I'm pretty pumped about it. Being 17, a laptop right now for college is perfect. The only problem is, I need tons of stuff off of my main PC in my room. I figured a LAN connection would be best because of the amount of information that I need to exchange. I have an Ethernet (sp?) cable that I got with my Xbox 360. Anyways, I matched up the ports on the two computers, plugged in the cable, enabled a LAN connection on my main PC, but I can only get the "Limited or No Connectivity" thing. I asked my dad about it, but he proceeded to tell me that Windows XP is an a**hole, that he's only ever been able to make two computers fully connect once, and if he goes in my room and tries to get it to work he'll probably end up breaking my laptop. Needless to say, I decided to try to figure it out on my own by hitting up some forums!

Thanks in advanced!:guitar:

.nICK.f.

BTW: I have a Dell Dimension 3000 for my home PC and my laptop is a Compaq nx 7400

[Edit]: BTWx2: The cable I'm using, I'm pretty sure, is a cross over cable. My dad said that it wouldn't matter whether it was a cross over or the other one because XP should recognize or whatever, blah blah, basically he said it wouldn't matter what kind I used but I figured I'd mention it here!

---

### Post by 3rdalbum on 2008-03-04
Are you using Ubuntu?

If so, you should set up a Samba server on the Ubuntu computer and share a folder. The folder can pretty much be anywhere on the computer. In the Network Neighbourhood on Windows, it should be able to see the share and you'll be able to log into it. Use the folder to transfer files between the computers.

---

### Post by superprash2003 on 2008-03-05
since you have connected a LAN cable from your computer to your laptop .. no IP address has been assigned to your windows pc.. hence it shows that limited connectivity thingy.. go to your windows pc.. go to control panel-network connections,right click on the lan card which is connected to your laptop, if you have only 1 LAN card .. then its gotta be LOCAL AREA CONNECTION.. right click on it.. and click on properties. and then go to tcp/ip properties.. and uncheck Automatically assign ip.. and enter the ip address manually.. set it up as say 1.1.1.1 .. then go to your ubuntu laptop... and click on system->administration->network and enter your password.. then select Wired connection(eth0) since laptops normally have only 1 ethernet port.. click on properties.. and incase roaming mode is setup disable roaming mode and choose STATIC IP ADDRESS as connection type and enter ip address as 1.1.1.2 .. subnet on both computer and laptop should be same so set both as 255.255.255.0 .. then for gateway set the gateway ip as 1.1.1.1  .. now the network has been created..
  Now if you want to share files you need to install Samba Server as the previous post says.. go here [http://ubuntuguide.org](http://ubuntuguide.org) it has a very easy to follow tutorial to setup samba server!!!

---

### Post by Iowan on 2008-03-05
You may not need to install Samba Server if you only need to access files on the XP box from Ubuntu (although I've read that you must install SMBFS).  If you intend to access files on the Ubuntu box from XP, then Samba Server will be required on Ubuntu.

---

