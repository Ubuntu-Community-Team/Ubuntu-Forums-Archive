---
title: "MSI Wind wifi troubles continue"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by kstella on 2008-10-23
I compiled the drivers as instructed in the [user wiki]("http://tinyurl.com/5bhk93"). I can detect networks, but I can't connect to any of them. :(

dmizer suggested in a [previous thread]("http://ubuntuforums.org/showthread.php?t=953148") that I try wicd instead of network-manager. I think it's great. :) But though wicd sees the networks, too, it stops in the middle of obtaining an IP address. I need to be able to roam. Any ideas?

Here's the device ID, in case that will help: ID 0bda:0158 Realtek Semiconductor Corp.

---

### Post by bradmurmz on 2008-10-23
Did you try using ndiswrapper? It's always a last resort for me because I try to avoid proprietary drivers and 'workarounds' but sometimes its the only option :(

---

### Post by kstella on 2008-10-23
Please explain for me - why (and how) would I use ndiswrapper if I've already compiled the drivers?

---

### Post by kstella on 2008-10-24
It worked fine for the folks in [this thread]("http://ubuntuforums.org/showthread.php?t=859073"), so I don't know why it wouldn't for me. :/

---

### Post by paullinux on 2008-10-24
[This]("http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Option_2:_Compiling_Drivers_for_the_Supplied_Wireless_Card") worked for me on my MSI-wind 100u.But make sure you do everything as stated with option2, including the copying of the files and such...

---

### Post by kstella on 2008-10-25
I did that before I posted this thread... Should I try again?

---

### Post by dizzy1kenobi on 2008-10-25
r u still having issues

---

### Post by infraction on 2008-10-25
> **kstella said:**
> I did that before I posted this thread... Should I try again?


I am in the same condition.  MSI Wind U100 with Hardy under WUBI.  Have followed the instructions for the driver compile under option 2 in the wiki, but modprobe does not find the device.  Device works just fine under Windows XP.

Why is this so difficult?

I would love a list of mini-pci wireless cards that Ubuntu supports 'out-of-the-box' so I could just replace the card and be done with this nonsense.

And, have I seen that Intrepid will support this RALink card??  Does anyone know for sure??  

And lastly......just how the hell do you access network-manager??

Appreciation in advance...you have my thanks!

---

### Post by kstella on 2008-10-26
Yes, still having issues. I post and then I try things at home, where I don't have an Internet connection. :/ If I do need Internet to download something, I bring the laptop to the office to use the wired connection there, but I can only do that some of the time.

There seems to be an updated version of the driver: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141/comments/93](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141/comments/93).

I don't completely understand the flow of that thread on launchpad, so it would be a great help to me (and now, infraction) if someone here at Ubuntu Forums could help us out. Thanks.

---

### Post by kstella on 2008-10-26
> **infraction said:**
> I am in the same condition.  MSI Wind U100 with Hardy under WUBI.  Have followed the instructions for the driver compile under option 2 in the wiki, but modprobe does not find the device.  Device works just fine under Windows XP.

Why is this so difficult?

I would love a list of mini-pci wireless cards that Ubuntu supports 'out-of-the-box' so I could just replace the card and be done with this nonsense.

And, have I seen that Intrepid will support this RALink card??  Does anyone know for sure??  

And lastly......just how the hell do you access network-manager??

Appreciation in advance...you have my thanks!

They're not going to support it in Intrepid, I've been told.

To access network-manager, I think System > Administration > Network.

---

### Post by kstella on 2008-10-26
Someone said that there was a BIOS update for the Wind. Would that and the updated driver help? I'd like to try, but I don't know the commands.

---

### Post by kstella on 2008-10-27
I found a [link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141/comments/93") to an updated version of the driver on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246141") and followed the [user wiki]("http://tinyurl.com/5bhk93")'s instructions again, replacing the old driver's name with the new. But it's still the same: I see networks, but I can't connect to them.

Is anybody out there? :cry:

---

### Post by didobuntu on 2008-10-28
Hello to all,

I dont know if this post is too late.
I personnaly used the instructions of this [link]("http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron") to make the wifi run on my msi wind .. I compiled it as explained .. and now the connexion rocks.

Also in the page, many ideas to make your favorite netbook more easy to use under ubuntu.

regards

---

### Post by kstella on 2008-10-28
> **didobuntu said:**
> Hello to all,

I dont know if this post is too late.
I personnaly used the instructions of this [link]("http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron") to make the wifi run on my msi wind .. I compiled it as explained .. and now the connexion rocks.

Also in the page, many ideas to make your favorite netbook more easy to use under ubuntu.

regards

Thanks, dido. Actually, that's what I did, and it didn't work. I tried with an updated version of the driver, and it still didn't work.

I'm feeling really bad about this right now - not your fault. It's just that I seem to have been posting to myself all this time. :(

---

### Post by pulsewidth on 2008-10-29
Hi:

I tried compliing the driver as well and had no success. So I followed the recommendations on the wiki at msiwind.net: I bought an Intel 3945 802.11a/b/g wireless card and replaced the stock Realtek unit. Result: instant success. Other MSI Wind users have also installed the Intel 4965 draft 802.11n card with success as well. If you don't mind spending $40 - $50 it's a lot less painless than compiling drivers with every kernel release...

---

### Post by kstella on 2008-10-31
It sorta works if I set static IP and DNS. But that's not what I want. I want to roam. :<

---

### Post by itisbasi on 2008-11-05
I followed the wiki ([http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron]("http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron") )too and had no problems compiling and using the drivers for ubuntu 8.10 on my new msi wind...

---

### Post by kstella on 2008-11-26
> **itisbasi said:**
> I followed the wiki ([http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron]("http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron") )too and had no problems compiling and using the drivers for ubuntu 8.10 on my new msi wind...

Are you able to roam?

---

### Post by ctwardy on 2009-02-10
Yes, I have the same trouble.  Some more details.

1. My card was basically working up until the upgrade to 2.6.24-23, using the "coffee" fork of the drivers. It would fail sometimes, and I think I had problems with nm and roaming, but usually at least a recompile-wlan0down-wlan0up (and maybe a reboot) got it working again.

2. Now, under either .24-22 or .24-23 (recompiling each time), I cannot connect to open or WEP networks, though I *can* connect to a WPA network. On WEP or open, it just hangs at "Obtaining IP address..."  I have upgraded to the newer drivers (2008-11-18).

3. I'm not sure it's the driver itself, but I'm not sure what else it might be. I have had no luck with nm, wicd, or trying manually.  On the other hand, I'm not sure what all is involved in "roaming" so I don't know what pieces are running.

4. Also, since the drivers worked for me before, and "just work" for other people, I suspect it's an interaction between several pieces. 

If someone has a good idea of what the pieces are, and how to disable them and try bringing things back one at a time, I'd be interested.  

FYI: I tried the precompiled debs from [http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html](http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html), but they wouldn't install for me, as I posted there -- some glitch in the .deb relative to my system.  (Besides, the kernel changes often enough it's just easier to keep recompiling. Well, when it works.)  

One possibility: the readme for this newest version mentions they wrote that for 2.6.27.  Other people have run it with 2.6.24-23, but possibly .27 would work better. 

I'm seriously considering the Intel card.

-crt

---

### Post by 090178 on 2009-02-18
A nice How to WIFI on Ubuntu guide is available here :

[http://www.mobvertising.com/blog/wi-fi-ubuntu-driver-ready-clicksurf/]("http://www.mobvertising.com/blog/wi-fi-ubuntu-driver-ready-clicksurf/")

The screen shots help me a lot.

It sounds this method is working on :

1     MSI Wind U100
2     RoverBook Neo U100
3     Advent 4211
4     Medion Akoya Mini
5     MyBook M11
6     Mivvy M310
7     Tsunami Moover T10
8     Casper Minibook
9     Datron Mobee N011
10    Proline U100 UMPC
11   CMS ICBook M1
12     HCL MiLeap MH 04
13     Axioo Pico
14     Averatec Netbook
15     Mouse LuvBook U100
16     Portátil Beep Iridium U10
17     Ahtec LUG N011
18     Sylvania MAGNI Netbook
19     Multirama HT Xpress Book
20     Positivo Mobo White
21     NTT Corrino 101I
22     Aristo Pico i300
23     Nuevo Visa Clip


Good luck

---

### Post by Eversmann on 2009-02-18
I have and advent 4211, and i got tired of the wifi with the rtl8187se card. So i order an intel 3945 mini pci-ex on ebay, installed in 5 minutes and no more problem with with on it. Works way much better and out of the box ;-)

---

### Post by snippyv on 2011-03-19
For the Advent 4211 try the GUI for Ndiswrapper and the Windows XP driver.

It worked for me.

---

