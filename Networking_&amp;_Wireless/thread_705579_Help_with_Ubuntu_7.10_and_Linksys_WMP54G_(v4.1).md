---
title: "Help with Ubuntu 7.10 and Linksys WMP54G (v4.1)"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by pauljs75 on 2008-02-23
Hello all. I managed to get an old computer working again by switching it to Ubuntu 7.10. :mrgreen: (Some odd reason XP failed to boot from the HDD one day, and wouldn't even read the XP install disk - which is mystery to me. I can only suspect the computer's previous owner got a nasty virus or two.) 

Anyhow back on topic...   After getting Ubuntu to work, I checked out the UI and thought all was good and fairly newb-safe. (Setting it up for my dad who isn't really attached to any particular apps or UI. Oo.o and Firefox should be plenty good.) But then tried to go online and nothing...

Seems the computer can see the router (an ol' Netgear that works ok with other computers) but refuses to talk to it.

I did some various things I saw posted elsewhere on Ubuntu forums in attempts to get wireless to work (various terminal commands or fiddling with ndiswrapper), but I'm not sure if I even dented the problem or made it worse. (Complete Linux newb here, so bear with me. Some stuff I tried may not have been for 7.10.) I learned a little bit about wifi, probably more than I care to know. (I just want the dang thing to work.) So I do know the wireless card is v4.1 based on the RT61 chipset.

Did some stuff in the terminal based on things I read, might have some useful info:
```
sudo iwlist scan
lo       Interface doesn't support scanning.
eth0     Interface doesn't support scanning.
wlan0    Scan completed:
            Cell 01 - Address: (gives mac addy for router)
                         ESSID: "Flying Spaghetti Monster"
                         Protocol: IEEE 802.11g
                         Mode:Managed
                         Frequency: 2.462 GHz (Channel 11)
                         Quality: 54/100   Signal level:-61dBm   Noise level:-96dBm

```

In addition to that, I also did an iwconfig...  Every field including and past link quality shows 0. I think those values are related to the funny behavior when using the taskbar-icon like thing to select a wireless - I can see the router and signal level at somewhere around 50%. But on the occasion I get it to connect, the little bars in the "taskbar" area are empty and signal level goes to 0%. Quite annoying, to say the least.

Basically if there are any instructions that have working links (seems some things have changed regarding what little I could find on Ralink RT61 drivers, which put me at a loss - being newb and all) and step-by-step directions specifically for Ubuntu 7.10 - that'd be great. Might have to revert to a fresh install before trying too, since I don't know if I "broke" anything in the last attempt to get wireless to work.

(Computer is located elswhere in the house, so I can't just do any direct updates or stuff like that. More or less any downloads I have tried involve running sneakernet via usb-stick and an XP computer. Need instructions that would work for that.)

---

### Post by Hightide on 2008-02-23
HI

this [thread]("http://ubuntuforums.org/showthread.php?t=588045") may help

:)

---

