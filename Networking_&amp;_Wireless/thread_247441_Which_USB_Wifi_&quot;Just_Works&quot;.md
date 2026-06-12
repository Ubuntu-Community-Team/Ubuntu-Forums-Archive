---
title: "Which USB Wifi &quot;Just Works&quot;?"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by rrnwexec on 2006-08-30
Can someone direct me to a USB wifi (802.11) dongle that "just works" in 6.06 without the need to add modules, download files, etc?

If not can we 'bless' (add code for) a couple of popular (and inexpensive) ones to work natively? In my opinion this would be a major boost to the overall usability of Ubuntu. Another good addition would if there were a utility that would automatically probe a connected USB networking device and present it's compatibility in easy to understand terms. Now I'm dreaming, right?

Cheers,
Randall.

---

### Post by alanmzifa on 2006-08-30
......a question i'd like to know the answer to myself.

You could try [this list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") but it looks unhelpfully out of date and wouldn't be sufficient to base a buying decision on in my opinion.

I suggested a thread or page **[[COLOR="RoyalBlue"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=246403&highlight=wireless+works+dapper+6.06")** that would act as a repository for devices that work with the **current** release and the important extra details required to make the device operate. I appear to be alone in thinking this way however as no-one responded in any way to the thread.

Looking through this section almost all the threads end up solutionless so the problem is immense. Unfortunately for most wireless is a deal breaker. I need to buy another adapter for a laptop I'm going to install Linux on as the sole OS and I'd quite happily patronise a manufacturer who could help provide a guaranteed OOTB solution. From what I've read on this section of the forum I wouldn't know of any I could confidently buy.

If you find one that does can you please post it back to this thread.

Thanks

---

### Post by jazzgossen on 2006-08-31
I recently bought a D-Link G122 and it works without after simply plugging it in. (However, I'm not getting anywheer near 54 Mbps, as I should. More like 4 Mbps. But I doubt that that has to do with the Linux drivers.)

---

### Post by tonab on 2006-08-31
i think alanmzifa suggestion is vry good and there is definetly a lack of support for wireless,i have posted on many threads only to be brought to a point and then never to hear from the help assistant again,and for a newb some of the info is way to complex,i have to say i think the .exe file is the best thing ever invented for computers and the gui of course,i cant help it,its just to darn complicated when one is typing commands and the reply is command not found,u need gcc, or autoconf,or kernel headers, and a lot of the time an internet connection, which is not possible if ones adapter wont connect in the first place,my suggestion to add, is a wireless distro of linux with usb in mind,as they are cheaper and easyr to connect,anyway i will soldier on with my complex array of information to get my usb device to work,and mayb all these posts will get some recoqnition,i suppose then one can start to explore admin, user accounts,virtual desktops and all the interesting things linux has to offer

---

### Post by rrnwexec on 2006-08-31
> **jazzgossen said:**
> I recently bought a D-Link G122 and it works without after simply plugging it in. (However, I'm not getting anywheer near 54 Mbps, as I should. More like 4 Mbps. But I doubt that that has to do with the Linux drivers.)

Thanks jazzgossen

This seems to be at least some progress. Can you confirm that you are running a default Ubuntu installation without any added kernel modules, ndiswrapper, drivers, or special configurations?

Cheers,
Randall.

---

### Post by rrnwexec on 2006-08-31
This one does not work:

D-Link
DWL-G132
H/W Ver.: A2
F/W Ver.: 1.02

---

### Post by rrnwexec on 2006-08-31
This one does not work:

U.S. Robotics
802.11g 54Mbps USB Adapter
Model: USR805422

---

### Post by rrnwexec on 2006-08-31
This one does not work:

Zonet 
802.11g USB Adapter
ZEW2501

---

### Post by rrnwexec on 2006-08-31
This one does not work:

blanc
802.11g Mini Wireless USB Adapter
Model: BW-54U11

---

### Post by rrnwexec on 2006-08-31
> **tonab said:**
> i think alanmzifa suggestion is vry good and there is definetly a lack of support for wireless,i have posted on many threads only to be brought to a point and then never to hear from the help assistant again...<snip>...i will soldier on with my complex array of information to get my usb device to work,and mayb all these posts will get some recoqnition,i suppose then one can start to explore admin, user accounts,virtual desktops and all the interesting things linux has to offer

I hope at some point a vendor steps up to the plate and offers a natively supported product. Are there any product managers out there who are willing to do so? Are there any readers here that know people at Cisco, D-link, USR, etc... that could introduce them to this thread?

Another thought I have is that we post a bug report for for each device that does not work natively. That will ensure that at least the Ubuntu crew knows what needs to be fixed. Bonus points if the bug database can somehow reference a manufacturer contact and kick out an email to them as a persistent nag. Thoughts?

---

### Post by alanmzifa on 2006-08-31
My thoughts on this are that it will probably be more use to other users if we post what *does* work rather than what doesn't. 

My thinking behind this is based on what I've seen on the wireless forum and the vast majority of threads unresolved that lead me (and aparently others too) to conclude that just about no wireless adapters work, or work properly, with Dapper Drake. I just want to know of an adapter that works and if there is one out there or several it would be in the interests of Ubuntu users to just know which to buy. I for one would prefer to buy an adapter that works for £30/$60 than spend the same amount of money + 20 hours trying to discover how to set it up and which may in the end be fruitless.

If adapters that work (with the current release) are listed together on a thread [like here]("http://www.ubuntuforums.org/showthread.php?t=246403") or an up to date wiki page that is specific to Dapper Drake only then not only does that save forum members considerable time but also acts as an incentive to manufacturers to eek out additional sales by supporting Linux. 

At the minute, from the threads we all see posted here, most users are experiencing similar problems and ALL are wasting time stumbling around in the dark, perhaps unneccessarily.

I realise many very clever Open Source developers are giving a lot of time to this, and I appreciate that, but I'm trying to suggest something that would save EVERY new Ubuntu wireless user a lot of heartache and wasted effort. 
Ideally it, or something like it, should be a sticky so that it can be the first port of call for new wireless users.

[click here]("http://www.ubuntuforums.org/showthread.php?t=246403")

---

### Post by jazzgossen on 2006-09-03
> **rrnwexec said:**
> Thanks jazzgossen

This seems to be at least some progress. Can you confirm that you are running a default Ubuntu installation without any added kernel modules, ndiswrapper, drivers, or special configurations?

Cheers,
Randall.

Yes. Default Dapper with kernel 2.6.15-26-386 on a Dell Latitude D800. No added ndiswrapper or other drivers.

---

### Post by tonab on 2006-09-05
i forgot to mention,im using ubuntu 5.10 breezy,and i just realised this thread is focused more on dapper,i hav tryd the adapter with debian,and ubuntu 5.10 with no success ,for above reasons mentioned, i havent tryd to get it on dapper as dapper refuses to install on my pc,im getting buffer I/O errors at installtion,but this is valid info as forums for different linux distro users are experiancing similar

---

### Post by lupine_nickt on 2006-09-05
[Ralink](http://www.ralinktech.com/) are recommended by the Free Software Foundation - they did, after all, release their drivers under the GPL.

The problem is that the drivers included by default in Dapper are incredibly old - for instance, the rt2500 (PCI) driver is a year old.

Personally, I'm running 2x D-Link DWL-G122 H/W Rev: **B1** (not A1 or C1!), and with the addition of 1 kernel module - which you can build from source or get from my repo [here](http://www.ubuntuforums.org/showthread.php?p=1464685) - they work "pretty well" (heavy p2p tends to knock them off right now, but a simple (sudo ifconfig rausb0 down; sudo ifconfig rausb0 up; sudo route add default gw <gw-ip>) brings them back without any problems. The (brand-new) rt2x00 driver, which - once finished - is bound to be far more stable, and compatible with Edgy (it needs a 2.6.17.9 kernel).

I've also helped quite a few people with rt2500 PCI/miniPCI devices, and again, they're pretty easy to get going.

Atheros are the other easy ones - there are drivers in the kernel, and they should work "out of the box"... especially ones based on the AR5005GS (e.g. the Gigabyte miniPCI card). Works like a charm for me. 

xF,

...Nick

---

### Post by lupine_nickt on 2006-09-05
> **rrnwexec said:**
> Another good addition would if there were a utility that would automatically probe a connected USB networking device and present it's compatibility in easy to understand terms. Now I'm dreaming, right?


Oh... your dreams may come true :). Pop along to [http://sourceforge.net/projects/wlan-magick/](http://sourceforge.net/projects/wlan-magick/) to see what I'm working on :)

xF,

...Nick

---

### Post by hockey1767 on 2006-09-06
The Airlink 101 Ultra Slim 802.11G USB 2.0 Works fine right out of the box.  Model number is AWLL3026.  The only thing I have noticed is you have the have the dongle plugged in when you boot up (doesn't seem to be hot swappable).  The card has a Zydas chipset.  I'm using the card right now running under Kubuntu 6.06.  One that does not work however, is the Netgear MA111.  I hope this helps.

> **rrnwexec said:**
> Can someone direct me to a USB wifi (802.11) dongle that "just works" in 6.06 without the need to add modules, download files, etc?

If not can we 'bless' (add code for) a couple of popular (and inexpensive) ones to work natively? In my opinion this would be a major boost to the overall usability of Ubuntu. Another good addition would if there were a utility that would automatically probe a connected USB networking device and present it's compatibility in easy to understand terms. Now I'm dreaming, right?

Cheers,
Randall.

---

