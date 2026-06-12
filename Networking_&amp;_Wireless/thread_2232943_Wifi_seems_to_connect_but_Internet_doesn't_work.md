---
title: "Wifi seems to connect but Internet doesn't work"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by edward8 on 2014-07-05
I understand that this is a very similar question to many others but I have been reading other discussions and still haven't found a good solution.

I've got an Eee PC Seashell series, running Ubuntu 14.04. The internet works through an ethernet cable to my router but when I use wifi, it seems to connect (the icon lights up) but the internet doesn't work. It is strange because the computer used to work with an old wifi router in my old flat. I've attached the tar.gz file from the [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) page about "before posting": [ATTACH]254482[/ATTACH]

The command
```
lspci -nn -d 14e4:
```

Gives the following
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
```
I previously consulted a page on Broadcom wireless cards, which suggested my card should work without installing anything else.

Pleae forgive my inexperience with this. I'll be very grateful for any help!

---

### Post by kc1di on 2014-07-05
Hi Lars and welcome to Ubuntu,

Please see my [post here]("http://ubuntuforums.org/showthread.php?t=2232939").

---

### Post by edward8 on 2014-07-05
Hi Dave,

I'm looking at the menu but it only has two choices: use the Broadcom 802.11 Linux STA driver from bcmwl-kernel-source - or to not use the wifi card at all. The first option was already chosen. Should I look for an alternative driver? If so, where?

Thanks so much for your help!

Ed

---

### Post by kc1di on 2014-07-05
ok Ed, 
follow the suggestion on [this post. ]("http://ubuntuforums.org/showthread.php?t=2232939&p=13065964#post13065964")

---

### Post by varunendra on 2014-07-06
> **edward8 said:**
> I previously consulted a page on Broadcom wireless cards, which suggested my card should work without installing anything else.

..yes, it should work without installing anything else, but as per the report, you have the proprietary "wl" driver installed, which is *supposed* to work with this card, but sometimes doesn't. If you didn't install it intentionally (from "Additional Drivers" or following some guide/post), it could have been installed during Ubuntu installation if you selected "Install Updates" option.

I suggest you get rid of it with the following command in a terminal (Ctrl-Alt-T) -
```
sudo apt-get purge bcmwl-kernel-source
```
..and reboot. Does it jump to life? If not, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) . Please note that it is a modified script, not the one that you already have.

---

### Post by edward8 on 2014-07-07
Dear Varun

Your advice worked - so simple, but I'd never have thought of it myself. Thanks for taking the time to help me!

Best wishes

Ed

---

