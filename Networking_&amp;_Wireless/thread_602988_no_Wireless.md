---
title: "no Wireless?"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by fragstar on 2007-11-04
I've just recently fresh-installed Ubuntu 7.10 (Gutsy Gibbon) and I'm having an issue.

when I open 'network settings' the 'wireless' option is missing. Meaning that the only network options I have for internet connecting are 'Wired' or 'modem'. 

I'm using a D-link WUA-2340 USB wireless adaptor in attempts to connect with my home network. I know that the adaptor I am currently in possesion of isn't officially supported, as per the wiki, but there was a post here: [http://ubuntuforums.org/showthread.php?t=420815&page=3](http://ubuntuforums.org/showthread.php?t=420815&page=3) that indicated the adaptor could be used. Since I was already in posession of one I decided to give it a shot.

The driver installed nicely, using ndiswrapper, and now when I use the -l command with it I recieve this message:
> neta5agu   : driver installed
                        device ( 07d1:3a08 )   present
still, no 'wireless' option. So I've been attempting various things all day to see if I could get this to work, yet to no avail. It would be a great help if anyone could help me.

or just tell me to get a supported adaptor.

either way, thank you in advance.

---

### Post by Mike Armstrong on 2007-11-04
I have struggled and finally succeeded in getting a Linksys wusb54gsv2.1 to work after 2 whole days and so many attempts that I now can recall my 128bit WEP key from memory.
However a tip for those with less free time or a requirement for sleep, a desktop with an ethernet card fitted and some money! Buy a wireless range extender, set it up from Windoze then plug your ubunto machine into the rj45 socket on the extender via a network cable, set eth0 in system>admin>network for DHCP et voila!  If you eventually get your machine to work with a wifi card or adapter of some description you can always use the extender to connect your Xbox 360 and the rangefinder will almost certainly cost less than the Xbox wifi conector and so do Bill out of a small bit of cash, Sad but satisfying.

---

