---
title: "&quot;Configuring network interfaces&quot; slows boot load times"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by ZeldaFan on 2007-05-27
When my HP dv9000t laptop boots, it usually takes a considerably long time. Usually I hear it should take around 30-40 seconds to boot, but mine takes well over a minute, probably nearer to two minutes. However, on the bar during the boot screen that shows loading progress, it progresses quickly, until one point, where the progress halts for around a minute. I guess whatever is trying to load at that time is slowing my computer down. I found out that at that time, the computer is "configuring network interfaces", and I am not connected to any networks (besides a wireless one for internet). Is there anyway to prevent it from taking so long to load, or is there any way to disable the operation? Or do I need it to continue to use my wireless internet connection?

---

### Post by spin2cool on 2007-05-27
One inelegant solution is to hit CTRL-C at the 'configuring network interfaces' step, which will kill that process and allow the boot to continue.

---

### Post by floke on 2007-05-27
Better solution. Edit the file itself and comment out un-needed entries.
sudo nano /etc/network/interfaces

(good idea to backup file first - sudo cp [original] [backup name])

For me I added # before every entry except 'lo' (which I think has to be kept free) and wi-fi (I think).

Then reboot and enjoy faster startup.

If this doesn't work you might have to remove the # and re-enable network lines if you need them.

Worked a treat for me. Cut my bootup from over 2 mins to under 1 min.

Hope this helps.

---

### Post by ZeldaFan on 2007-05-27
My "interfaces" file reads this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
I, being a more or less beginner with Ubuntu, have no real idea what all of this means. I see the "lo" part you've been referring to. But I dont see the wifi part. How should I edit it to decrease boot times.

---

### Post by floke on 2007-05-27
Add an # to every line except the 'auto' and 'iface' lines belonging to lo and wlan (just for luck)

So you are commenting out every line belongng to eth0-2 and ath0

That should do it (with luck!) - If not, just remove the #'s and this will restore it.

---

### Post by floke on 2007-05-27
BTW: This assumes you are using wi-fi rather than ethernet (sorry I forgot to mention this). If you are using ethernet then you should of course leave your connection (eth0 eth1 etc.) with no #'s.

---

### Post by ZeldaFan on 2007-05-27
Actually after experimenting a little bit, it turned out that it wasn't wlan, it was eth1 that I had to leave uncommented. Anyway, though, but leaving it uncommented it allowed me to still use wireless internet. however, my boot times didn't decrease all that much. If i comment eth1, my boot times decrease to around 20 or 30 seconds, but I cant use my wireless internet. So, I dont really know how to fix that, because I think that by enabling wireless or something during my boot, it takes some time. I dont know why it is taking so long to do that though.

---

### Post by chili555 on 2007-05-27
Any chance you have an ipw3945 card? If so, please see bug report here: [https://bugs.launchpad.net/ubuntu/+bug/108152](https://bugs.launchpad.net/ubuntu/+bug/108152)

---

### Post by ZeldaFan on 2007-05-27
Yes I have do have an ipw3945 card, and as I've said, I've concluded the problem is occurring due to eth1. But still, when i comment out that line, the OS boots faster, but my wireless internet network stops working. What do i do then?

---

### Post by chili555 on 2007-05-27
What happens if you leave eth1 commented out and then, after you have fully booted, do:```
sudo ifdown eth1 && sudo ifup eth1
```Thanks.

---

### Post by ZeldaFan on 2007-05-27
So will I have to type in that code everytime or just the first time.

---

### Post by chili555 on 2007-05-28
Well, you will have to type it in at least once to see if it actually works. If it does, we will try putting it in rc.local to see if that solves the problem. If not, we will try other approaches. 

So, did it work?

---

### Post by ZeldaFan on 2007-05-28
Oddly enough, I didn't even have to type in the code you told me to type in. I just commented the lines corresponding to eth1 and for some reason, while my boot times reduced to around 15-20 seconds as expected, my wireless still was working. I think the reason that my wireless didn't work before even though I commented eth1, was because I didn't comment both lines. Anyway, it works, and my boot speed is astonishingly fast. Thanks a lot!

---

### Post by davidme on 2007-06-19
This config worked for me:

> auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


---

### Post by AndrewNi on 2007-06-19
I have that exact same config as posted above and yet it still takes one minute to finish configuring the network interfaces. My wireless card is using ndiswrapper but it is the bcm4306 card, no problems as such. When I comment the eth0, ath0 (used for a different removable card) and the wlan0 interfaces from the interfaces file the boot takes no time at all, but there are no network interfaces. :/

---

### Post by peakpc on 2007-06-27
Thank you soooooooo much for posting this tweak. My setup ended up looking like the one above (after trying a few others) and I have shaved a full minute off my boot time!:D

Compaq V5000 custom 2gig Turion 1gig ram ATI 200m Broadcom 4318 Ubuntu 7.04 XGL Compiz  
Boot time was 2.17minites now 1.20!!

---

### Post by peakpc on 2007-06-29
Maybe I spoke to soon, results seem inconsistent. I thinks that it may be related to DHCP timming out on whatever is not connected. I have no prof as yet but I am going to try some changes soon.

---

### Post by peakpc on 2007-07-04
For those of us using ndiswrapper to make our wireless go, try this,

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

modprobe ndiswrapper

auto wlan0
iface wlan0 inet dhcp

this seems to work consistently for me:)

---

