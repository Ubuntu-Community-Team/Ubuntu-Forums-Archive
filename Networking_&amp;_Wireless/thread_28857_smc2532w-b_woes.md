---
title: "smc2532w-b woes"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by somuchfortheafter on 2005-04-21
anyway i have this card supposedly can work off the orinoco driver included in ubuntu and it can however the instructions on patching the driver for monitor mode do now work and they return errors, trying to compile or even install the .deb version of wlanng fails as well. is there any hope of getting this to work at all?

---

### Post by zencoder on 2005-08-05
I believe one of the more recent **hostap** packages may have a driver that can put this in monitor mode and work.

My employer uses this card w/ kismet for wifi audits.

---

### Post by zencoder on 2005-08-09
OK, so after dicking with this for a few days, I can't seem to get it working either.  Anyone able to help a Debian/Ubuntu n00b with some module building and such?

---

### Post by zencoder on 2005-08-17
Ok, so after much trial and tribulation, I finally got this worked out, with some help.

You can use the hostap_source.deb from the Ubuntu repos or the source from the hostap site.  I downloaded the source.

You'll need the kernel-headers for your kernel, plus all the build packages.

After I unpacked the source, and did the **make && make install** as root, I still couldn't get the card to work.  I had to add the following to /etc/pcmcia/hostap_cs.conf
```

card "SMC2532W-B EliteConnect Wireless Adapter"
  manfid 0xd601, 0x0010
  bind "hostap_cs"

```

Restart pcmcia and hotplug daemons/services and reset/reinsert the card, and you should be good.

---

### Post by alan.clements on 2005-09-05
Yes well that got the green light to blink. But it still didn't get it to work ...  :-x 

After several hours of ->  ](*,)  I was trying to find a gui thingy that would do a simple point and click on an access point and volia it would attempt to connect. Imagine my surprise when NONE of them actually worked. They either require stuff that isn't in the standard release of Ubuntu or the couple that did work didn't actually connect to anything. All I wanted to do was connected to a simple network!

I tried placing the card in Ad-Hoc mode and I could see the the access points but nowhere did I find a suggestion to use the access point switch for iwconfig! 

I tried this 
```
 iwconfig wlan0 essid "flyingj" channel 1 mode Managed key off ap 00:0C:30:F7:B3:3E 
```

imagine my surprise when i did an **ifconfig** and got an IP address!    ;-) 

now if Ubuntu can do this Auto magically we'll be there.  Unfortunately no project I've looked at yet seems close.

---

### Post by herot on 2005-11-08
yes these instructions worked well for my SMC2532W-B also

thanx :)

---

### Post by zencoder on 2006-02-06
[http://www.ubuntuforums.org/showthread.php?t=126229](http://www.ubuntuforums.org/showthread.php?t=126229)

I've written a short HOWTO for building the hostap-source package for Breezy 5.10.  Not sure how effective the card + hostap is for networking, but I use it for wardriving and penetration testing for clients, and it works fabulously.

---

