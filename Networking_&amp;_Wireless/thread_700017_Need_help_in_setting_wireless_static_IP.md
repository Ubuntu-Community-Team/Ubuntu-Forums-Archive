---
title: "Need help in setting wireless static IP"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by Guanno on 2008-02-17
Hi,
I'm new to Ubuntu... just installed Ubuntu 7.10 on my T41 IBM laptop and have been trying to create a wireless static IP. I'm using WPA2. Every time I used the GUI (nm-applet 0.6.5) to set up the network connection, I can't use the net at all. The only way I can surf the net is through roaming mode. I've tried the guides on this forum and other sites but it is either too complicated/confusing or that it simply doesn't work. Can someone help me with the setting up of wireless static IP?

Thanks.

---

### Post by amohanty on 2008-02-17
Hey.

First off when you say static IP you mean a static IP as far as your LAN is concerned or a static IP as far as the world is concerned? If it is the former, most routers come with DHCP (dynamic IP) by default. However by default the leases on most IPs as granted by the DHCP servers are (usually) forever, practically guaranteeing your laptop a static IP as far as the local LAN is concerned.

If its the latter, then you need to map the WAN (world visible) static IP to a LAN static IP and then setup your router (if yours lets you do so) to assign the LAN IP to the MAC address of your laptop. I would strongly recommend against this unless you are absolutely sure you know what you are doing.

If the above sounds a bit confusing please post back with more details of what you have? what you want to do? and optionally why?

HTH
AM

---

### Post by Guanno on 2008-02-17
Thanks for the reply. There are many computers connected through the router and each computer has their own IP. So I guess I'm doing the former, LAN static IP, instead of the world. I've been trying to set a static IP for my IBM laptop, but it nvr worked. Either I get disconnected or the laptop connects through a different IP than what I wanted.

---

### Post by kaginken on 2008-02-18
First, as mentioned earlier, most routers that assign dynamic IPs usually never change them anyway, so you may want to just go with the flow and use whichever one the router assigns to your laptop, chances are it will never change anyway, or if it does, it wont be very often, as in years...

If you really want that static IP - then you can definitely make that work.  If you're working with the gui nm-applet Network Manager, be sure your /etc/network/interfaces doesn't contain ANYthing except the loopback.  Mine looks like this now:

auto lo
iface lo inet loopback

That's it.  If nm-applet sees any interfaces listed in there except the above two lines, it will ignore them.  

Oh yea, and good choice with the IBM Stinkpad, I've got the exact same one and love it.  It all works very well with ubuntu.

Rock on!  :guitar:

---

### Post by kevdog on 2008-02-18
Cant do it with network manager in gutsy.  I believe Hardy is going to release a version that is capable for nm to work with static IPs.  For Gutsy, you got three options,

#1 Dump nm - use wice
#2 Set you parameters in the /etc/network/interfaces file as specified by Weiman01: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
#3 Set all parameters on the command line: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by gigaferz on 2008-02-18
I have static ips in my 3 computer 2 wireless and one wired.

You need to log in to your router set up web page and  assign yourself an ip address.

---

### Post by amohanty on 2008-02-18
As mentioned by Kevdog, you will need to set it up manually in /etc/network/interfaces (its easier that way). 

In a terminal do:
man interfaces

to see what you need to do to set it up. 
Basically you might need something like this (assuming you interface is called wlan0

auto wlan0 # will bring it up automatically at boot
iface wlan0 inet static # use a static ip for interface/card
address 192.168.x.xxx  # ip
netmask 255.255.255.0 # most likely netmask  
essid your_router_ssid 
mode managed # for most routers
key xxxxxxxxxxxxxxxxxxxxxxxxxxxx # whatever encryption jey you are using

HTH
AM

---

### Post by kaginken on 2008-02-18
I'd try sticking with network manager, i've not had any problems with it on any of my wireless machines and they all have gutsy except one, and it's running 6.05 dapper drake and network manager works on it too!

As far as KevDogs suggestion - may be a winner, but I'd stick with the network manager and do the kevdog method only as a last resort.  That manual method can be a real pain, especially if you're wanting to connect to multiple wireless hotspots...

Not to knock the kevdog - sounds like he knows what he's talking about, I'm just debating the realms of insanity and reality and their effects on the human mind...:)

---

### Post by Guanno on 2008-02-18
Hey,

Thanks for all the advice! I've tried editing the interface but nothing worked. I either didn't do it right, or it just doesn't work. Anyway, finally found another network manager called Wicd (didn't find anything on Wice as suggested by Kevdog but hope it was a typo and meant Wicd instead) and dumped nm. Managed to setup static ip easily without dealing with the console or anything. Problem solved...and I hope it doesn't crop up ever! Thanks...

Anyway, just recently installed Ubuntu on the Stinkpad cos it's been trashing a lot when it was on XP. Heard Ubuntu is a better OS, so gave it a try. Trying to get the hang of it...

Cheers.

---

### Post by kaginken on 2008-02-18
Guanno,

You hang in there - I've been using ubuntu for about a year, and can now do EVERYthing I used to do in XP.  It was a lot of fun learning what the best XP replacements were too...  Now, I'm single booting ubuntu, ripping/burning, streaming, connecting to multiple wireless networks, printing to different printers, automating backups, u name it, I'm a true 'power user'.  

Patience is all it takes, and you will be rewarded!

Godspeed.

---

