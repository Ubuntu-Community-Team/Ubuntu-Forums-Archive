---
title: "Realtek RTL8180 Wireless LAN (Mini-)PCI NIC"
date: 2004-10-30
forum: Networking &amp; Wireless
---

### Post by borru on 2004-10-30
I have Edimax EW-7126 wireless Wifi card but it wont work with Ubunutu.
Ubunutu does detect the hardware... It shows proper (as chipset) Realtek RTL8180 Wireless LAN PCI NIC 
 in device manager.

---

### Post by az on 2004-10-30
That is because there is no open-source driver available from the company.

Have you tried ndiswrapper?

Install ndiswrapper-utils

and then install your windows drivers with
sudo ndiswraper -i WHATEVER.INF

Load the module 
sudo modprobe ndiswrapper

Then check to see what you got:
sudo ndiswrapper -l

If you have a device, then try 
dhclient wlan0

To load the module on boot, add ndiswrapper to your /etc/modules file.

---

### Post by kinoth on 2004-11-01
Actually, there are 8180 chipset drivers available from Realtek, but I can't seem to get them to work.  When I follow the directions (both in the readme and at [http://www.linuxvoodoo.com/resources/howtos/linksysv4/](http://www.linuxvoodoo.com/resources/howtos/linksysv4/), which I'm roughly following), I get a few pages of makefile errors.  I've tried both version 14 and 15, and have followed both sets of directions closely. Has anyone gotten these drivers to work, or must I go the ndiswrapper route?

---

### Post by mduduzi on 2004-11-01
The last time I checked, Realtek 8180 was only supported on 2.4 -even at that with minimum interest. The best I did was get to forget that card --it's hardly worth the time. If your card is new, rather return it and swop for something with the Atheros AR5212 chipset or so. If you can't then the wraping of Windows drivers is about all you can do and I did not try that.

Many people are still new to Linux, but the large vendors are not. If they do not release drives or code for Linux, it's a business decision on their part --why loose sleep over that?

I hope you come right eventually.


[QUOTE=kinoth]Actually, there are 8180 chipset drivers available from Realtek, but I can't seem to get them to work.  When I follow the directions (both in the readme and at [http://www.linuxvoodoo.com/resources/howtos/linksysv4/](http://www.linuxvoodoo.com/resources/howtos/linksysv4/), which I'm roughly following), I get a few pages of makefile errors.  I've tried both version 14 and 15, and have followed both sets of directions closely. Has anyone gotten these drivers to work, or must I go the ndiswrapper route?[/QUOTE]

---

### Post by mduduzi on 2004-11-01
Check this out.. They are still on 2.4.2

We've been on 2.6 for about a whole year now....

[http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)

---

### Post by ljoris on 2004-11-24
[QUOTE=mduduzi]Check this out.. They are still on 2.4.2

We've been on 2.6 for about a whole year now....

[http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)[/QUOTE]

Yes, and it's actually built on a RedHat 7.3 system ... duh!

Does anyone know of tools to do some, no knowledge required, port of 2.4 drivers to a 2.6 kernel tree ?

Moreover, for a couple of days now i've been working on getting such a rtl8180 card to work on a suse 9.1 or something system. Besides the fact suse is a very hard to figure out distribution to do manual configuration with and yast2 just isn't cutting it this time and other time too allready ... the machine actually just locks up ... or the kde-environment locks up then after some irregular interval the whole system goes kabonka's. 


Since this is not really distro specific i wondered if none of you experienced similar issues when using ndiswrapper or the rtl8180 card.

---

### Post by darrell on 2004-11-24
[QUOTE=ljoris]Yes, and it's actually built on a RedHat 7.3 system ... duh!

Does anyone know of tools to do some, no knowledge required, port of 2.4 drivers to a 2.6 kernel tree ?

Moreover, for a couple of days now i've been working on getting such a rtl8180 card to work on a suse 9.1 or something system. Besides the fact suse is a very hard to figure out distribution to do manual configuration with and yast2 just isn't cutting it this time and other time too allready ... the machine actually just locks up ... or the kde-environment locks up then after some irregular interval the whole system goes kabonka's. 


Since this is not really distro specific i wondered if none of you experienced similar issues when using ndiswrapper or the rtl8180 card.[/QUOTE]
 I spent days, if not weeks, a year or so ago trying to get various versions of the realtek linux driver working with various kernels. I finally a combination that worked, for my router/firewall machine, but it was very painful, so that has been running 2.4.something ever since - until a few days ago...

I decided it was time to upgrade my router/firewall machine to 2.6, so I installed ubuntu, and looked for updated realtek drivers - none available from what I could find. But ndiswrapper worked like a dream.

I installed ndiswrapper through synaptic, and then followed the instructions in the ndiswrapper wiki [http://ndiswrapper.sourceforge.net/wiki/index.php/Installation](http://ndiswrapper.sourceforge.net/wiki/index.php/Installation) from the point Installation - 2. install your windows driver, to the end.

---

### Post by bsammon on 2005-04-22
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

---

### Post by kubuntuuser on 2005-08-16
Hi I am actually on hoary, but have finally just got this card working on my system after many failed attempts.

I was following the instructions given on the wiki page listed above but it still wouldn't work. 

I have a couple of tips for other who are using it too. 

when you set  the essid and subsequently check it, i found that it will still display off/any when you do iwlist until i set my wep key.

I also found that the XP driver works best and can be downloaded from the Edimax website.

I also found that doing this

[FONT=Courier New]sudo iwconfig wlan0 key s : password [/FONT]

instead of 

[FONT=Courier New]sudo iwconfig wlan0 restricted key s : password [/FONT]

as recommended made the card work and i could enable the interface correctly. 

Hope this helps, but if it has confused instead, i apologise. 

I will upload a script i wrote to configure and enable the card when I am back at my linux box.

---

### Post by jon_herr on 2007-02-18
WPA is the way to go... too bad everyone is 'happy' with WEP.

I've been trying to compile the 2.6 version of this driver from realtek but keep having problems with the makefile.  That's a separate issue, which I'm working on over here:

[http://ubuntuforums.org/showthread.php?p=2176180#post2176180](http://ubuntuforums.org/showthread.php?p=2176180#post2176180)

It's hard to not be negative about that other 'hatted' distro when they are holding Linux progress back by forcing people to use old kernel versions in order to have driver support...  

In some respects the 'hatted' distro defines what support is given by hardware vendors - not unlike the Redmond company...  but I rant.

I really like ubuntu... it's amazing to me that having package management wasn't an obvious requirement from the beginning of linux.  Ease of application and driver installation would have had linux on more desktops than all of the Windows competitive OS's combined.

Yet the need for tar file extraction and source code compilation (as in this case) makes some experiences with linux continue to be very frustrating (again thanks to the hatted distro).  If I were a complete newbee I'd be turned off...  but I have faith in the future of linux thanks to ubuntu.  Keep up the great work!

<Soapbox mode off>
:popcorn:

---

### Post by bowerymarc on 2007-02-27
> **mduduzi said:**
> 
We've been on 2.6 for about a whole year now....

[http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)

Has anyone else tried this driver with an SMP kernel?  I'm running 6.10 with the 2.6.17.11-generic kernel on an Intellistation Pro-Z dual Xeon.  When my network usage goes over 50%, the machine freezes.  The higher over the quicker.  If it hits 100% it freezes almost immediately.  By freeze I mean the screen and everything freezes, including the mouse pointer, even the fan speed... machine responds only to the power button.  So it's like when it crosses over to using the second CPU, there's a lock condition which eventually manifests...

I've tried various combinations of things, it's narrowing down to the network card (a cheapo PCI wifi card)

here's the dmesg fyi:

[17179598.696000] rtl8180: Initializing module
[17179598.696000] rtl8180: Wireless extensions version 20
[17179598.696000] rtl8180: Initializing proc filesystem
[17179598.696000] rtl8180: Configuring chip resources
[17179598.696000] rtl8180: Memory mapped space @ 0xf0015000 
[17179598.696000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[17179598.696000] rtl8180: This is a PCI NIC
[17179598.696000] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[17179598.704000] rtl8180: Card MAC address is 00:13:f7:3b:17:5a
[17179598.720000] rtl8180: EEPROM version 105
[17179598.720000] rtl8180: Card reports RF frontend Realtek 8225
[17179598.720000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[17179598.720000] rtl8180: WW:use it with care and at your own risk and
[17179598.720000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17179598.720000] rtl8180: Energy threshold: b
[17179598.720000] rtl8180: PAPE from CONFIG2: 6
[17179598.720000] rtl8180: IRQ 58
[17179598.724000] rtl8180: Driver probe completed
[17179598.868000] rtl8180: Bringing up iface
[17179599.076000] rtl8180: Card successfully reset

---

### Post by Titus A Duxass on 2007-02-27
Oops

---

### Post by bowerymarc on 2007-02-27
> **Titus A Duxass said:**
> Oops

WTF?!?!?!?!

---

### Post by Titus A Duxass on 2007-02-27
> Quote:
Originally Posted by Titus A Duxass  
Oops 

WTF?!?!?!?! - I really should not try posting before I've drunk coffee.

---

