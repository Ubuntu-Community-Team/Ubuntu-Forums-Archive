---
title: "No Wireless N?"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by xantonin on 2008-06-28
Hi, I have a Dell XPS M1530 with the Intel 4965 AGN wireless card.

My router is a LinkSys WRT600N Dual Band router. GBN 2.4 GHz / AN 5 GHz

I couldn't get it to connect wirelessly for the longest time and couldn't figure out the problem, I thought I had the wrong drivers.

After thinking about it for a while though, I realized the problem. It wasn't connecting because my router was set to function in Wireless N ONLY mode on the 2.4 GHz band.

So I tried Wireless N on the 5 GHz Band, no go. I switched both bands to Mixed mode, and it connected fine with A on 5 GHz and B/G on 2.4 GHz

What do I need to do to get Wireless N to work?

Thanks

---

### Post by John Silverton on 2011-06-20
Interesting, this is the same question I had. 
Obviously, there is NO ANSWER to this problem, as the question was asked four years ago!!! 

Not much help here... 

Looks like I'm stuck with an expensive, now-obsolete router... with NO way of using it with Ubuntu...

Looks like it's time to enrich Bill Gates bank account again; and go back to (gag) Windows.

Thanks Anyways,

John Silverton

---

### Post by superduperlinuxperson on 2011-06-20
amazing

---

### Post by garvinrick4 on 2011-06-20
> Looks like I'm stuck with an expensive, now-obsolete router... with NO way of using it with Ubuntu...
> What do I need to do to get Wireless N to work?That would be the iwlagn driver by intel for linux.
It does not support N and is not going to as I understand it. It is just very unstable.
It does use the "N" in the 3.0 generic kernel that I have in 11.04 and 11.10
Other kernels you have to set router in Mixed mode "G" and "N" in 2.4 Ghz and also 20 Mgz in 2.4 and can use the 40Mhz in 5 Ghz with N only.
and then add this config file to modprobe.d as below.
```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Now put this line in below and hit save and reboot:
                                 [COLOR=#000000][FONT=Times New Roman][SIZE=3]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT][/COLOR]
 
basically disables "N" while in this kernel of Ubuntu and works at 54Mb/s in "G" which gets around pretty quick.
when you run this code you will now see.
```
iwconfig
```intel bg card instead of bgn card:
#Remember if you are running a version of Ubuntu that can use the 3.0 kernel then
just install it and you will get the "N".
Have to just open the /etc/modprobe.d/iwlagn.conf and delete the line you inserted and hit save
and now the card will accept the "N" again.
#Below is link for 3.0 kernel (need 3 of them headers, all deb and image of whichever one you use 32 or 64 bit.)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-rc2-oneiric/")

---

