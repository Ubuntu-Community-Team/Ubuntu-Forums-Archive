---
title: "TP Link TL-WN321G (rt73) just won't work in Linux(?)"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by RostokMcSpoons on 2008-01-27
Hi guys

Basically I've given up on trying to get this to work under Linux.

I thought I'd share my experiences of this device and Linux, in case it helps other people.
I've tried these distros:

Ubuntu 7.10 Gutsy (twice)
Ubuntu 7.04 Feisty
OpenSUSE 10.3
gOS

(all 32bit versions)

And I've tried the both the Serialmonkey drivers, and the WinXP drivers in ndiswrapper.

My router is a SpeedTouch 585v6, hard wired into my main pc, running in the same room 4ft away from my 2nd pc.
The 2nd pc's spec is: Athlon64 3700 / 2gb ram / Asrock Dual-SATA2 mobo / Ati x800xt-pe (no ati driver loaded) / Western Digital 120gb hard drive (whole disk given to Linux)
I also tried it on my ancient IBM Thinkpad (Pentium 2) which is running Puppy Linux, and it failed to work on that at all.

I've had lots of 'near misses' where it's worked for a bit, and then it's either a) not worked after a reboot or b) gone down mid-session and I've not been able to bring it back again.  
Scan results would often 'lose' my router, but still see my neighbours'.   And the indicated signal strength fluctuated between 0 and 80%.  

(I'd like to point out that [gOS](http://thinkgos.com/) was the only distro that ran the wifi straight after installation - no messing with other drivers or ndiswrapper.   I'd recommend anyone having problems with their wifi to try it - it runs as a LiveCD.)

I'm a Linux noob so there's obviously a strong possibility I've messed up in following the instructions posted in various threads on these forums.  Though the fact it *sometimes* worked suggested I was either very close... or had done it correctly. 
So... up until 4 hours ago I thought maybe I'd just got a broken wifi dongle.  But tonight I've 'borrowed' an *ahem* 'evaluation' copy of WinXP Pro, installed it, and the dongle has worked absolutely flawlessly.  And it's reporting 100% signal strength all the time :)


In summary, I wouldn't be at all surprised if some people are using the WN321G quite happily.  But I can also understand anyone who's having a nightmare trying to get it to work ;)   The rt73 drivers seem to be problematic as it is, it probably doesn't take much - a hardware or configuration problem - to tip it firmly into the 'never gonna happen' camp :(


Finally I'd like to thank everyone who tried to help on these forums - I do appreciate it, ta :KS

---

### Post by ikki_72 on 2008-05-26
This guy just did it:
[http://www.linuxquestions.org/hcl/showproduct.php/product/3778/cat/myprod](http://www.linuxquestions.org/hcl/showproduct.php/product/3778/cat/myprod) and i'm gonna  try it too.

---

### Post by guildofghostwriters on 2008-06-04
I use TL-WN321G wireless dongle without any real problems. I followed the 'how to' at the top of this page (post #11): [http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2](http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2)

It doesn't seem to like network manager however so I got rid of that and all the bits related to it (nm-applet, for instance, off the top of my head) and am using rutilt. The only minor problems are irritations rather than real problems. The only way I can get rutilt to save/load profiles is if I run it as root thus:

```
sudo su
sudo rutilt
```

I'm pretty newbie so perhaps other people can tell us if that is/isn't a terribly risky and bad thing to do. The alternative is to enter SSID and key manually every time I connect. The other irritation is that certain updates (I think linux kernel updates - ones that require a restart anyway) will get rid of the drivers so that they're no longer listed in the restricted drivers thingy (or whatever it's called in Hardy) and I have to follow the how to again to get it working. But apart from those two small irritations, it works fine.

---

### Post by guildofghostwriters on 2008-06-04
Actually, I've just noticed that the guy who did that rt73 how to has replied to a thread about how to make rutilt save and load profiles - it's post #7 here: [http://ubuntuforums.org/showthread.php?t=803520](http://ubuntuforums.org/showthread.php?t=803520)

---

