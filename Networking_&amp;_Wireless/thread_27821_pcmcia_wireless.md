---
title: "pcmcia wireless"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by XanonimX on 2005-04-17
I've been trying to use my wireless but I have some problems; I've tried to follow (amog others) [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto/view?searchterm=ndiswrapper](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto/view?searchterm=ndiswrapper)

using lspci I get:
(...)
0000:06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

It is a WPC54G Linksys PCMCIA

I folowed all the steps of the manual (installing ndiswrapper, downloading the codecs) but after doing 

ndiswrapper -i lsbcmnds.inf

if I do: ndiswrapper -l
I get:

Installed ndis drivers:
lsbcmnds        invalid driver!

And I can't follow other steps

Any solution? Thanks

---

### Post by spd106 on 2005-04-18
The BCM4306 chipset is used on many different oem branded cards. Belkin, Linksys and Dell to name but a few. I suggest following the links on 

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

and trying out some the drivers from there.

To begin with stick to the rev 3 versions.

Also look at this thread
[http://ubuntuforums.org/showthread.php?t=25643](http://ubuntuforums.org/showthread.php?t=25643)

A known problem with the bcmwl5*.inf drivers are that the radiostate is set to 1 when it should be 0. You will find lots of posts about this.

I hope this helps

---

### Post by XanonimX on 2005-04-18
...mmmm....
sorry...

 :| 

I didn't have the .inf file but not the .sys file....

If someone has the same error: find the .sys file that is in the same direcotry of the drivers and put it in the same place than .inf

newbie errors...

Sorry and thanks

---

