---
title: "can't get wireless internet to work"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by ireallydontcare on 2009-02-12
heya
installed ubuntu 8.10 yesterday and now im trying to get the wireless to work.
ive put on ndiswrapper and i think the driver is installed.
the network tab thing has 'enable wireless' as being ticked

but it wont automatically detect the wireless router and if i try to type it in it just doesnt work.

not sure what to do now...

please help

thanks!

---

### Post by mandeepsmagh on 2009-02-12
I am running 8.10 and wireless worked out of the box. You need to check what hardware you are using for wireless and post it here. Only then some one can help u .

---

### Post by NoBugs! on 2009-02-12
Did you look in System - Admin - Hardware Drivers and see if something needs to be enabled?

You should see what network hardware you have by running:
```
lshw -C network
```

---

### Post by Ice Man on 2009-02-12
I'm using the same Ubuntu and also have a problem, My laptop is a Toshiba Satellite and when I connect to the NetGear wireless if often shows as connected but after say 30mins it just stops working.
It still shows as connected but the internet doesn't work.
The other 2 computers work in the office off the same wireless and if I switch to Windows on my Laptop no problem.

IS there a Bug in my Ubuntu, any way of fixing this??

---

### Post by abyssius on 2009-02-12
> **Ice Man said:**
> I'm using the same Ubuntu and also have a problem, My laptop is a Toshiba Satellite and when I connect to the NetGear wireless if often shows as connected but after say 30mins it just stops working.
It still shows as connected but the internet doesn't work.
The other 2 computers work in the office off the same wireless and if I switch to Windows on my Laptop no problem.

IS there a Bug in my Ubuntu, any way of fixing this??

Although the experts who volunteer to provide help on this forum are IMO unrivaled, I'm pretty sure they must get tired of painfully teasing information out of those requesting help -  and also repeating instructions that have been posted many, many times before. I suggest you follow the instructions in the following link. Following this advice when requesting help for a wireless problem gives you a much better chance of receiving a meaningful reply.

[http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

---

### Post by trikster_x on 2009-02-12
EDITED: Sorry, I got on the wrong post.

---

### Post by Ice Man on 2009-02-13
> **abyssius said:**
> Although the experts who volunteer to provide help on this forum are IMO unrivaled, I'm pretty sure they must get tired of painfully teasing information out of those requesting help -  and also repeating instructions that have been posted many, many times before. I suggest you follow the instructions in the following link. Following this advice when requesting help for a wireless problem gives you a much better chance of receiving a meaningful reply.

[http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

Thanks for the link but as an Absolute Beginner I'm still not able to understand a lot about this Ubuntu stuff. I have a friend who helps me out, but he also doesn't know much about the Wireless stuff.

Let me try to go through this more;
I use a Toshiba Satellite L310 Laptop and I am using is Ubuntu 8.10 (intrepid), I use NETGEAR Wireless internet which is shared with 2 other computer, but both using Windows. 
When I first connect to the wireless using my Laptop is connects and works no problem.

Then after a short time it still shows as connected but nothing works Internet wise.

I disconnect and try to reconnect but after the disconnect it won't reconnect. I Shut down the computer and re-start the computer and re-connect and it works. But then the same will happen and I have to go through the above again.

Any help or links to solve this problem will be appreciated.

---

### Post by Neural oD on 2009-02-13
what I found for me was that for some reason my wired connection would mess up the wireless one - even if it wasn't plugged in. On the command line - try this: sudo ifdown eth0
or  whatever your wired connection is - u can get the info by typing: ifconfig
on the command line. 
Another solution - is that people have installed wifi-radar because the network manager at the moment can be problematic

---

### Post by Ice Man on 2009-02-13
Ok thanks for that, will give it a go

---

### Post by Neural oD on 2009-02-13
> **Ice Man said:**
> Ok thanks for that, will give it a go
in my setup - I have it that the wired network does not start up automatically - so if I need it then i start it - saves you from shutting down the wired connection each time. Here is a portion of my /etc/network/interfaces file - I have disabled eth0 from starting automatically.
```
#auto eth0

iface eth0 inet dhcp
	address 192.168.1.48
	netmask 255.255.255.0
	network 192.168.1.0
#	broadcast 10.0.0.255 
```

---

### Post by Neural oD on 2009-02-13
just a quick note - that first line in the code should read: ```
iface eth0 inet static
```
that's if u want a static ip - otherwise leave the dhcp there - then the rest of the lines are irrelevant - as you would be getting your ip from a dhcp server

---

