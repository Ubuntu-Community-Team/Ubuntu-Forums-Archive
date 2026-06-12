---
title: "Cannot Connect to internet after reinstall..."
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by Miki01 on 2006-09-29
Okay, on my first install I was helped by another member and refered the code

> $ sudo /etc/init.d/networking restart

It worked the first time. When I boot from the Kubuntu liveCD, internet works fine.

I had to re-install Ubuntu 6.06 a few times due to some problems. The 2nd install my network was quickly found and the installation configured it all for me. But there were errors, etc later on, so I needed to reinstall...

This is my 3rd time reinstalling it and this time, the installer didn't configure my network connection...

Again, I tried
> $sudo /etc/init.d/networking restart

But to no avail...

I had eth0 configured to DHCP and activated it and tried the code again, all I got was:

> miki@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/04:4b:80:80:80:03
Sending on   LPF/eth0/04:4b:80:80:80:03
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/04:4b:80:80:80:03
Sending on   LPF/eth0/04:4b:80:80:80:03
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]


So I deactivated eth0 and setup and activated eth1... What I got was similar:

> miki@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/04:4b:80:80:80:03
Sending on   LPF/eth1/04:4b:80:80:80:03
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

Does anyone know what's wrong? Why is the LiveCD working fine and the actual install being sleezy? And how come on one install my network was auto config'd correctly and not this time? 

Thanks to all who reply.

---

### Post by gn2 on 2006-09-29
I have had similar problems. If the network set-up stage of the installer failed I found it impossible to fix it later.

I had to persist till the installer's network auto set-up eventually worked OK.
This took me many tries.

I see you have an AMD 64, are you using 64-bit OS? 
Never used it myself, but have read reports of it being a bit fussy.....

---

### Post by morphodone on 2006-09-29
I've made the mistake of not plugging in my ethernet cable...

Be sure to check the easy stuff too.

If no dhcp is being offered it may not be ubuntu's fault.

---

### Post by Miki01 on 2006-09-30
Yeah, I know I have my cable plugged in, since it works when I'm in XP...

I don't want to have to go through trying to re-install dapper again, since I've already tried just getting to that network setup screen in the initial startup, and after about the first ten times, enough was enough...

morphodone, what do you mean by it not being Ubuntu's fault? It works perfectly fine, and my download/upload speeds are fast when in XP, how is it that it doesn't even work in Ubuntu? Its the same computer... Do you have any other ideas?

---

### Post by morphodone on 2006-10-01
What kind of network cards are you using?

---

### Post by Miki01 on 2006-10-06
I'm using the motherboard intergrated gigabit LAN port.

EDIT:

I also just read a thread about ways to go on fiddling with something called forcedeth to fix it. Apparently, after doing a search, I couldn't find anything related to forcedeth.

Why is it that when I boot the Kubuntu from the CD, I can access the internet just fine, like with XP. But with Ubuntu Dapper, it just doesn't do anything, just says that the "persistent database is sleeping"...

Why is it that the other computer in the room can also work through that router? There are currently 3 computers connected into that router, but when I boot to Dapper, it just doesn't do anything... 

I even tried pinging 192.168.0.1 and 192.168.1.1, as I don't know my router's IP. All I received was that it wasn't reachable... This is even after I restart the router and let it affiliate itself with the MAC address of my computer's LAN port.

Help is GREATLY appreciated...

---

### Post by morphodone on 2006-10-06
If you have an nvidia based motherboard there is a known issue
when dual booting with windows xp.

See my post [here]("http://www.ubuntuforums.org/showpost.php?p=1563747&postcount=12").

---

### Post by Miki01 on 2006-10-07
Ah, okay, thanks. The first time I installed Ubuntu, it was before I installed Windows, but at the time, it itself didn't work properly without an initial network reset. After that, it worked like a charm. A while later, I installed Windows and after a few months, my Ubuntu partition got corrupted through user error. So I installed Ubuntu again, and it worked like a charm, internet and all. But after another user error, I had to reinstall it. This is the current time installing it and it doesn't work. Well, I hope something gets around this fix. I'm going to try the PSU thing now.

EDIT: The PSU technique worked. I am editing this message from Ubuntu now!

I hope that when I boot into WinXP then reboot and go to Ubuntu, that it works fine.

Thanks a lot for your help.

EDIT: Just tested, I can boot back and fourth from XP to Dapper and the internet connection works great! d/ling torrents now!

Thanks a lot!

---

### Post by claesbrandt on 2007-07-10
Just want to add something. In the post "Daulboot Installation . no more Network controller", mentioned above, morphodone states that you must wait 15-30 seconds before booting your machine again and that you need to switch the button on the power supply or unplug the power. I tested on my laptop (in docking station), that I only need to make a cold boot. That is, I shut down Windows, the machine turns off by itself, I start the machine right after into Linux, and my ethernet card is alive again. I could see it on the lights on the card. They simply wouldn't light up when warm booting from windows into linux. Making a cold boot the lights turn on right away.

Hope this helps and thanks for the great tip. I was getting really tired of this issue :-)

---

