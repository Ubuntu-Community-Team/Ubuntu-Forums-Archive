---
title: "Can't install ndiswrapper, No ethernet card only wifi"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by zoozabar on 2007-03-02
Hello Forum,

this being my first post I hope I get this right. I am trying to install the my wifi card as I want to get some updates for Ubuntu 6.10 like different apps and such. It seems that the only way I can accomplish this is with my PC directly connected to the internet. 

Now the problem, about 6 months ago my built in ethernet card on my dell laptop stopped 't working and I have tried several drivers and it just won't work. Ubuntu recognises the card but does not recognie it properly I guess...

02:00.0 Ethernet controller: 3Com Corporation Unknown Devise fbff (rev 78)
            Flags: bus master, medium devsel, latency 32, IRQ 11
            I/O ports at ec80 [size=128]
            Expansion ROM at 24000000 [disabled] [size=128k]
            Capabilities: <access denied>

so now onto the wireless card and low and behold I need to install a special driver to get it to work. this is whay Ubuntu says about it...

07:00.0 Network Controller: Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller (rev 02)
            Subsystem: Lynksys Unkown device 0049
            Flags: bus master, fast devsel, latency 64, IRQ 11
            Memory at f8000000 (32-bit, non-prefetchable) [size=8k]

Also as a last note I would try to boot into windows and download what I need but I seem to have lost the ability to boot into xp, and I have already tried to repair the MBR to no avail so I figure its no big deal, as soon as I get Ubuntu going I may not need xp anymore.

Now for the real question, is it possible to download ndiswrapper from a different computerand then burn it to a disk or USB thumb drive to then install on my laptop?

any help would be greatly appreciated!

---

### Post by Floppyjoe on 2007-03-02
If you have the Ubuntu install disk you can use that to put ndiswrapper on your computer by clicking System/Administration/Synaptic Package Manager.
Then click Edit/ADD CDROM.
Then click reload.
Then search for ndiswrapper.

Floppyjoe

---

### Post by zoozabar on 2007-03-02
Thanks now that I have that installed I need to find out where windows installed my bcmwl5.inf file any ideas?

---

### Post by zoozabar on 2007-03-02
nm new problem I will post in new thread


I was able to successfully install ndiswrapper though thanks for the help!:guitar:

---

