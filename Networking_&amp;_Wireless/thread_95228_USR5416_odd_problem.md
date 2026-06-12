---
title: "USR5416 odd problem"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by vmalep on 2005-11-26
Hi everybody,

I recently installed a computer with Ubuntu 5.10. Everything is going fine. Even the U.S.Robotics Wireless Turbo PCI Adapter (USR 5416) works (I had to specify the righ channel in the config file).

However, I observed that times to times, this interface losts the connection to the accesspoint. I tried to restart the network daemon, but it does not solve the problem. I tried "iwlists ap", etc., but the adapter does not find anything on the network, even though it is up with the right IP address etc. So far, the only way I found to reconnect the  adapter to the accesspoint is to restart the computer...

Any clue?

Thanks in advance,
Pierre

---

### Post by Dr. Nick on 2005-11-29
Try **sudo ifdown wlan0** the **sudo ifup wlan0 **in a terminal,That may re enable your connection without restart. Not sure why it drops though. Are you using wep? Ive heard ndiswrapper to be better than the acx111 drivers so you may have better luck just usin ndiswrapper. Dont have the card though so I cant help much more. Just relaying what ive seen [here]("http://www.ubuntuforums.org/showthread.php?t=20298&highlight=TI+ACX+111")

---

### Post by ruudiculus on 2006-02-04
I've got an odd problem too with my USR5416 wlan card. Stupid enough I solved the problem in the past installing Kubuntu, but now I switched to Ubuntu and I'm doing the circus all over again ;) (I now write down EVERYTHING I do on linux)

So, ok; here it comes.

[LIST=1]
[*]Just from a new Ubuntu I installed **ndiswrapper-utils**
[*]I got the usr11g drivers found on [www.linuxant.com](www.linuxant.com) (they don't modify them do they :-k )
[*]I followed the ndiswrapper instructions, resulting in the message "usr11g driver present, hardware present"
[*]ndiswrapper is now linked to wlan0, modprobed and all
[*]When I run **iwlist wlan scanning** it says "wlan0 No scan results"
[/LIST]

I'm writing this on my laptop which is next to my Desktop with the non-working wlan, so there definately are essid's in the air and I can connect to it.

So, the problem is in the Desktop PC. What I've done next is:
[LIST]
[*]I've de-installed ndiswrapper as described in the ndiswrapper wiki
[*]I've installed ndiswrapper version 1.8 from source
[*]I've re-installed the windows drivers again, modprobed etc.
[*]The **iwlist wlan0 scanning** result is still the same:
[/LIST]

I've changed the channels from 1-12 back to auto with no result. 
lsmod returns: ** wlan size: 120988 used by: 0**
I checked the BusID's: they match
I tried all variants of **iwconfig** with no luck

I'm quite out of ideas and I don't remember how I did it the last time with Kubuntu :confused: 

But I know it worked! Has anyone gone through (and solved) the same problem and WRITTEN DOWN the trick?

---

### Post by DreamWearl on 2007-01-10
Did you found the solution to your problem?
(or anybody else)

i'm having the same problem...

thx!

---

### Post by sh4d0w on 2008-02-09
i have the same  card but different problem , i can see usr8054 access point on my list and when i am trying to connect on it  my system is freezing forever and if i don't remove the wlan card from my pc ubuntu cant login it stops to the nfs system read.

---

