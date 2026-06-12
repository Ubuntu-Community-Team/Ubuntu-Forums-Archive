---
title: "Quick WPA-PSK  help"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by bsf on 2007-06-20
Okay, i am new to Ubuntu, well 2 weeks maybe and so far it has been great... well cant say that because i haven't been able to do anything on it! so my question.

What is the easiest way to use WPA-PSK (tkip) encryption in ubuntu, my usb/driver allows me to use it (TL-WN321G) but the original network manager that comes with ubuntu won't let me have it, only WEP. My driver works well in WEP but i need WPA-PSK as it is more safe :p.

thanks to all that help!

---

### Post by kevdog on 2007-06-20
First install wpasupplicant from synaptic or aptitude.

As far as getting wpa working -- you are treading dangerous waters.  I dont know of a consistent solution that works for everyone.

Ill give you two methods
#1. Consult the Stick by Wieman located at the top of the networking and wireless section.  A lot of different options here.  They have worked for me particularly when needing a static IP.
#2. Ive also used this method -- its probably the smplest -- but Ive recommended it to others and it has not worked for all people. [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Either way make sure to keep back-up copies of your /etc/network/interfaces file.  Each method alters this file and if something goes wrong, you can always restore a working copy

---

### Post by bsf on 2007-06-20
i have a dynamic ip i think.

---

### Post by ugm6hr on 2007-06-20
> **bsf said:**
> What is the easiest way to use WPA-PSK (tkip) encryption in ubuntu, my usb/driver allows me to use it (TL-WN321G) but the original network manager that comes with ubuntu won't let me have it, only WEP. 
What happens when you try and connect to a WPA network? Are you sure you have enabled roaming on the Manual Settings page?

Network Manager gives a list of networks before asking for the passphrase - and if it recognises your network, will offer WPA as an option.  If your card does not support WPA, then it will simply try to connect / authenticate indefinitely.

If you can't get this resoved - it's worth trying Wicd instead of Network Manager before resorting to manually editing the settings.

---

### Post by kevdog on 2007-06-20
ugm6hr

I tried WICD also, but really never got it to work for me.  I tried the stable release -- Ive heard actually more problems with that release than the beta release -- any way the GUI tool for me was no good.  It opened but whenever I hit a button the gui froze and I had to kill it through ps.  The documenation on how to setup wicd, unlike network manager where there is too much information, is scant.  I could register with the wicd forum, but I couldnt even post due to a bug in their BB. I noticed that many of the posts were old.

Im not trying to knock WICD, Ive read its worked for many, just not for me.  Just one man's opinion but I thought wieman's wpa how-to stick was very well written and seems to work for many, but not all people.  rt drivers seems to be a big problem.

---

### Post by ugm6hr on 2007-06-20
kevdog

I had major problems with Wicd v1.2.7 (stable) and found v1.2.9 a lot more stable (with Feisty).  Documentation is sparse (is there any?) - but it's not hard to get it to work (if it can be made to work).  All I needed to do (for the 2 systems I've used it on) was select the correct network interface (e.g. ath0 rather than wlan0) and the correct wpa-supplicant driver (e.g. wext rather than madwifi) in preferences, click on the correct network arrowhead and enter security data.

My suggestion was simply because it's quick easy to install and try (for people who like GUI) - and almost as easy to remove if it doesn't work.  And it allows roaming too.  Downsides: no ability to disconnect (only chose a different network to connect); it messes up the connection when resuming from suspend (which I don't use).

Linux (and free software) is all about choice, isn't it?

---

### Post by kevdog on 2007-06-20
I couldnt agree more -- maybe I will try it again.  I like tinkering a lot but wireless (because I dont have a wired connection) is a painful thing to tinker with if you are wrong.  A lot of reboots, and from what Ive found although you might reinstall networkmanager the same way you had it before when it was running (at least I think so), it never seems to work the same except by adding another tinker.

---

