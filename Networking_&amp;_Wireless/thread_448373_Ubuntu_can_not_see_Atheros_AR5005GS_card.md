---
title: "Ubuntu can not see Atheros AR5005GS card"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by SimonT on 2007-05-19
Hello all I have jumped in to the world of linux and need some help to stop me drowning.

I am trying to setup my Ubuntu on my Toshiba M2 laptop. At the moment I am cheating a little and useing Vmware under windows XP. One I am happy with linux I will dump windows and move to just useing Ubuntu.

Every thing works fine apart from my wirless card under windows it is reported as

```
Atheros AR5005GS Wireless Network Adapter
```

I tried to follow the [ Atheros AR5212 Madwifi HowTo ]("http://ubuntuforums.org/showthread.php?t=38972")  but after the reboot when I type in iwconfig I do not see any cards displayed


what worries me is that when I run lspci I dont see the card

[[IMG]http://img95.imageshack.us/img95/5567/lspciuf6.th.png[/IMG]](http://img95.imageshack.us/my.php?image=lspciuf6.png)

any helps or hints or points to read please let me know

---

### Post by ugm6hr on 2007-05-19
I have an Acer Aspire 5051 with the same WLAN card.  Xubuntu detected it automatically though.  It does require use of the Restricted Drivers (in Xubuntu: Applications -> System -> Restricted Drivers Manager) - it's listed as Atheros Hardware Access Layer (HAL).  It obviously needs to be ticked, or it won't work.  Just to make sure - you haven't turned it off from the hardware, have you (i.e. from BIOS or external switch)?

---

### Post by SimonT on 2007-05-19
I just checked and just saw the vmware host controler listed no sign of any wireless cards.

---

### Post by ugm6hr on 2007-05-19
The lack of entry on lspci is a bit concerning - sorry didn't notice that first time.  It should be listed as:
08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

And if it works in Windows, that is very bizarre.
Might be worth booting from the LiveCD again to see if that recognises it on lspci (cos it should).  

If not, I'm out of ideas...

---

### Post by SimonT on 2007-05-19
Yes looks like a vware issue as I botted direct from the live cd and was ble to do a iwconfig and see the wiresless card. Not sure where to turn now

---

### Post by ugm6hr on 2007-05-19
Sorry can't help with that - I don't even know what vmware is!  But all the issues will disappear if you reinstall Ubuntu fresh.  XP will continue to dual boot without a hiccup.  GRUB even recognises any "hidden" recovery partitions to make restoring (Windows) easy if necessary.

---

### Post by SimonT on 2007-05-19
Vmare allows you to boot in to one OS and then boot up another OS at the same time running 2 OS's at the same time you can jump between bother of them and they can talk to each other it is pretty good :-)  But as I found out this morning useing wireless is not supported it can be tweaked to see the wirless network but will never be able to talk direct to the wireless card.

Looks like I had better take the jump and see how to get windows XP and Ubuntu duel booting

---

