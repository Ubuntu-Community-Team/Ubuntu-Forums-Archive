---
title: "Wifi disabled by hardware switch upon suspend"
date: 2016-01-09
forum: Networking &amp; Wireless
---

### Post by daniel280 on 2016-01-09
I know this is a pretty common problem on these forums but I have been looking for a solution on and off for months and still haven't found anything that fixes it. I'm running Ubuntu 14.04 on an HP Pavillion notebook. Whenever I close the lid or suspend my laptop I am unable to reconnect to the internet unless I reboot, when I click on the network icon in the top right of the screen it say 'Wifi disabled by hardware switch'. I have no problems when I first boot up in linux or at any time when I'm running Windows. 

Using rfkill list when the wifi is not working produced the following:
> 2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


Using rfkill unblock has no effect on it.

I have also tried using >  ifconfig wlan0 up  which resulted in: >  SIOCSIFFLAGS: Operation not possible 

I have also tried running >  rfkill event  while I suspended the computer to see if I could pinpoint the time at which it is supposedly hard blocked. When I woke it up it had written the following
> 1452331012.258749: idx 0 type 2 op 0 soft 0 hard 0
1452331012.258765: idx 1 type 1 op 0 soft 0 hard 0
1452331017.446733: idx 1 type 1 op 1 soft 0 hard 0
1452331029.334892: idx 0 type 2 op 1 soft 0 hard 0
1452331031.467645: idx 2 type 1 op 0 soft 0 hard 1

I couldn't really tell if that was at all useful..

Could it be an issue with the drivers for the wifi?? I haven't tried reinstalling them or anything yet because I wasn't really sure how to do it. 

If anyone has any ideas I would loooove to hear them, this has been a thorn in my side for too long!!

---

