---
title: "How to set up a XP and ubuntu network?"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by the lemming on 2007-05-16
I have just installed ubuntu onto my laptop.

Could somebody please tell me how to set up a home network with my ubuntu laptop and my Windows XP PC?

The reason that my PC does not have Linux is because I've yet to find one that a beginner (me) can use which actually works on my PC.

Both computers can happily access the internet through my wireless router which is WEP encrypted.  I'd love WAP but WEP is the common denominator between both systems.

Cheers

---

### Post by Nythain on 2007-05-16
are you wanting to share files... is that what you are gettin at, samba is your solution

---

### Post by tact on 2007-05-16
What sort of internet connection (home network) do you have currently? 

I have broadband connected at my house.  The ISP supplied a PPPoE "modem" that provides a single ethernet port at the back end.  It needs a software "dialler" to run it and is designed for a single Window's box to connect.   So....

I bought a Netgear WiFi, firewall, router, PPPoE dialler, all-in-one box.  It can be configured to do the PPPoE dialling.  It connects to the ISP provided PPPoE "modem" via an etnernet port and and brings up the broadband link to the ISP.

As well as driving the PPPoE modem,  the Netgear router makes 4 ports available for wired connections as well as the Wifi facility.   My wife's WinXP laptop connects to the home LAN.   My ubuntu laptop does so also.  We share files/folders occasionally.  We both access the internet however we like (wired or wireless).

There are a dozen other ways to do things, times several different types of internet/network connection options...

Don't know if that answers your Q?

---

### Post by the lemming on 2007-05-16
Thanks for the replies.

All I want my home network for is to share files.  My PC has a shed load of stuff and my Laptop is just too small to store all my MP3, JPEG digital maps and the such like.

I'm hoping to have something which is idiot proof so that I can swap files and stream movies and music to my laptop.

I'll check out Samba.

Cheers

---

### Post by tact on 2007-05-16
Ok...  so all the good stuff is on the WindowsXP PC?  And you just want to access it inside your ubuntu laptop.

Dead easy.  :)  Samba is installed by default in ubuntu anyway.  Installed "enough" so that you can click on Places>Network and see any and all windows PCs already.  No need for you to do anything.  No need to edit configs or install anything.

Windows networking sometimes takes a while before all the shares are published properly (even when its an all windows network - its a windows thing, nothing to do with ubuntu).   Be patient.  Shares will show up eventually.

If you want to push the matter and you know how to find out the Windows machine name, and/or its IP address - then you can type in the machine name or IP address in the address bar of the Network browser...

eg...   if your winbox is 192.168.0.7 then typing this in the browser address bar...
smb://192.168.0.7/
will find it fast.

Provided you have shared out the appropriate folders/drives in the windows box then you will be able to access the files in your ubuntu machine.

---

### Post by commbot on 2007-05-20
wrong post

---

