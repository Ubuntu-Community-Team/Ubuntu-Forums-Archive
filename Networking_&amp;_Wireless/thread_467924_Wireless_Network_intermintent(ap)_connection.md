---
title: "Wireless Network intermintent(ap?) connection"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by dardack on 2007-06-08
Ok i'm gonna post this only because i couldnt' find an answer.  I have Ubuntu 7.04.  Newly linux convert (haven't booted into XP in 4-5 days now).  My issue is i periodically loose internet over my wireless.  I have tried 2 separate wireless, one Linksys WUSB11 v2.8 and the BestBuy PCI one (i bought it because 1 on sale $30. two i'm an instant gratification type of guy, and 3. i read that it works right out of box).  With the USB one i'll see the bars drop to 0% (but still lists the ESSID just says 0% next to it) and after a bit goes back up.  The PCI never drops to 0% i'll just be playing WoW and all of a sudden nothing i'll go to the other workspace and try firefox and it has nothing, few seconds comes back up, but by them I'm either dead, or if it's an escort quest quest objective is failed.  This wouldn't be a problem if i just was online broswing/email but with WoW PITA.  I'm hoping someone can give me some commands to run and we can figure this out.  I really dont' want to have to boot into XP to play WoW, i mean as far as FPS goes it's great.  And i'm sure if i sat down and did a heavy intensive internet browsing session it would get on my nerves then also.  

One thing, with the USB i couldn't get the manual configuration in Network-Manager to work.  I had to leave it on ROAMING mode.  Should i try to turn this off with the PCI card?  With Roaming does it periodically drop the connection?

Any type of help to resolve this would be great.  Thanks.

---

### Post by dardack on 2007-06-08
OK so i read teh bug report here:  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821)

Seems to be issue with network manager.  Can anyone point me to a place on how to uninstall this and set up the wireless manually?

---

### Post by dardack on 2007-06-09
So it seems to be Network-manager.  I went into synaptic and unistalled it.  Than i have to manually run:
sudo iwconfig ath0 key 111acad(whatever)
sudo dhclient -d ath0


I've tried putting this in a bash script (which does work if i manually run it) and put it in my sessions for startup, but it doesn't seem to run.

The only thing is i have no signal meter.  Anyone know of a plugin just for that?

---

