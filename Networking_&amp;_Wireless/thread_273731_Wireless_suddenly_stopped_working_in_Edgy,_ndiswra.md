---
title: "Wireless suddenly stopped working in Edgy, ndiswrapper and native"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by joehill on 2006-10-08
I was using wireless just fine this morning, then I went to campus and restarted and found it didn't work.  I don't think I upgraded or touched configuration.  It still doesn't work on my home network either.  I was using ndiswrapper with Intel's neti2220 driver, but then I tried two cards with native support (they show up as eth1 instead of wlan0) and I have the identical problem.

Network manager has never worked for me on Edgy, but if I use the old gnome "network settings" dialog, it doesn't show any networks as being available and it doesn't even try to configure when I enter the name into the dialog manually. If I connect with iwconfig on the command line, all 5 signal-quality bars appear and it says 100% signal strength, but still nothing works.  iwconfig/iwlist still act like everything's normal.  But there's no connection.

So it's apparently not a problem with ndiswrapper (which is usually what doesn't work). Yikes! Even if there's a fix I can't upgrade because I can't connect (even my wired connection doesn't seem to work).

Oh, and another thing--something really strange is going on.  If I modprobe -r ndiswrapper, wlan0 goes away for a split second and then comes back, even if network-manager is disabled.  If I disconnect a network device, a second later it looks like it's connected to something, even though iwconfig lists it as off.  No matter what I do, something is taking over the nework connection and overriding anything I do.

---

### Post by unco on 2006-10-08
I had similar problems recently in that wireless stopped for no reason, and I use ndiswrapper, but my problem not exactly the same.  Here are some of the things I found.

1. I had a working wireless connection then after installing something completely unrelated (scanner I think), my wireless nolonger worked.

Had to investigate and think that creating a /etc/default/wpasupplicant file and putting in the OPTIONS line may have been the key.  But this only affects WPA encryped set ups.

2. In my /etc/network/interfaces (which was setup manually with static IP addresses, GUI didn't work for me) I had eth0 and wlan0 and they were in that order (had to manually change eth1 to wlan0 to match the ndswrapper settings).

I found whenever I restart my machine and eth0 was unplugged, it overrides the wlan0 for local networks which were available over wlan0 ... I still could connect to internet thru wireless just not lan.

To fix I had to move the wlan0 settings above the eth0 settings in the /etc/network/interfaces file, and ever time I restart my machine I have to do this to get the wlan0 to access local network:
```
sudo /etc/init.d/networking restart
```
So I have just set up as a terminal command launcher for this, until I workout a better way that works.

Lastly even when the connection to the internet and lan were down.  I was always able to scan for the APs using iwlist wlan0 scan.

Wireless seems like a bugger to setup.  Goodluck

---

### Post by mOjO_420 on 2006-10-09
download ndiswrapper source from [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) and compile and install manually and it will work again.

---

### Post by joehill on 2006-10-10
I doubt recompiling nsidwrapper would work for me, as I have the identical problem with my two native wireless cards as well.  For the moment I'm back working with my Dapper partition, as Edgy is pretty much useless without any kind of functional networking.

---

