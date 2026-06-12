---
title: "Lniksys WUSB54GC - Disconnections all the time."
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by galvheim on 2007-12-13
Hi there,

I recently bought a Linksys wireless router with a linksys wireless USB adapter. It was found easily by Ubuntu during CD-boot and after installation both in the 64bit and the i386 version, but my problem seems to remain.  

It's as follows: 
When the system has loaded my wireless connection will not automatically connect to my wireless router. For connection I must left click on the icon at the top right and chose 
o Linksys  [signalstrenght] 
It then usually connects after just a few seconds. 
Then minutes and sometimes hours pass and suddenly it just drops the connection. The Icon changes from the usual signalstrenght-icon to a searching icon for then to just show a thing with a red forbidden-sign over it. I can then go manually and click on it to reconnect to the linksys network, but it will not work. 

What I have to do, and I'm really starting to get tiered of it, is to disconnect it from the USB and reconnect before manually tell it to reconnect to my wireless network. This is truly a pain in the ***, and just now in the past 4 hours I have done this around 5 times. It will hold the connection for just a few minutes or just an hour max. In some cases it has been holding up for several hours, but after some time when leaving the machine on while not home. After I come back it will work for a minute or two before having troubles again.

I've tried all my efforts to manually set up the connection with a static internal IP, but this will not work at all.

My settings are as follows. 
SSID: linksys (not WLAN)
No encryption.
Router IP: 192.168.1.1
DNS: 10.0.0.138
Searchdomain: lan

I've tried to add linksys to the searchdomain under DNS, but for some reason my Ubuntu will forget all my settings after i reset my computer, so why it's there I don't understand.

Any suggestions to fix this problem will be highly appreciated. I have installed Ndiswrapper, but where not able to install the driver via this. But this might be caused by me not having the correct .inf file, since my wireless USB-adapter is named WUSB54GC and the only driver i can find on the linksys page is named WUSB54GSC. 

Thoughts and help will be highly appreciated.

THanks in advance. 

Kind Regards,
Gunnar.

---

### Post by shruti on 2007-12-13
I wish I could help you but unfortunately, I haven't been able to get this same device working at all - in Feisty OR Gutsy :(

Two question to help you target the problem:
1. What version of Ubuntu are you using? (Feisty, Gutsy, another distro like Linux Mint)  I've had wireless problems with many cards, computers, and chipsets with Gutsy, and so I have downgraded for now
2. Have you tried the USB device with other computers and other operating systems (Windows, Mac, a non-Ubuntu or non-Debian distro ...)  and if so do you have the same problems?

---

### Post by coolbrook on 2007-12-13
--

---

### Post by galvheim on 2007-12-13
Well, we'll see how it will work now. I've just got it to work in Manual-mode by setting WPA Personal encryption. Maybe this will force it to log on automatically next time and every time. I am optimistic right now, and it has already worked without disconnecting for over 3 minutes :-)  Will reply on this if it was fixed.

For any reasons why it doesn't work, I can not help. It just does it on my system. Or at least Gutsy Gibbon will find the device, use it, but thus far it has been very unstable in roaming mode. So that's why I've set it up using manual settings which forced me into going into encrypted mode.

---

### Post by coolbrook on 2007-12-13
> **galvheim said:**
> the only driver i can find on the linksys page is named WUSB54GSC.

Some drivers are definitely better than others but don't change a thing if you've already found the solution.

[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859919492&packedargs=sku%3D1134691790190&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1949290190B03&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859919492&packedargs=sku%3D1134691790190&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1949290190B03&displaypage=download#versiondetail)

---

### Post by galvheim on 2007-12-14
After allmost 15 hours it my linksys has not yet disconnected. Therefore I figure that the problem is solved once and for all. 

The solution for me was to set up the network manually like with a WPA personal encryption of 123456## :-)

ESSID = linksys
type Password = WPA Personal
Password = ######## (8 digits)
Connection settings
Configuration = Static IP
IP adress = 192.168.1.100
Subnet Mask 255.255.255.0
Gateway = 192.168.1.1

Under DNS and DNS-servers i put 10.0.0.138 since my router is connected to Thompson  Speedtouch modem/router.

under searchdomains i put "lan" along with "linksys" - not sure if its used or not. I also set this in my router. 

 Anyway this works for me.And it seems stable. The next thing to try now is to reset the computer and see if it will automatically be connected using these same settings.

---

### Post by galvheim on 2007-12-14
From a little searching I found this. The reason is that I still, after each reboot has to manually activate my network. Irritating but it works.

[http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc]("http://ubuntuforums.org/showthread.php?t=516649&highlight=wusb54gc")

So I hope this will be a relief to my problems.

---

