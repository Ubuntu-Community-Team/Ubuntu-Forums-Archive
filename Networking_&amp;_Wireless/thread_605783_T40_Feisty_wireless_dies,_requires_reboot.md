---
title: "T40 Feisty wireless dies, requires reboot"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by bliffle on 2007-11-07
This IBM thinkpad T40 wireless sometimes quits after running for a while (a few  minutes to several hours) and requires a re-boot of the T40 to get going again. I haven't been able to find a way to re-start wireless short of re-booting the whole computer.

Is there an independent way to just re-start the wireless?

Is there some kind of software I can install to monitor, report and manage the wireless adapter?

---

### Post by realvz on 2007-11-07
sudo /etc/init.d/dbus restart

---

### Post by bliffle on 2007-11-07
I'll try that once I get the T40 connected again. Right now I'm working from a T60 from the Gutsy 7.10 liveCD.

I found something called "wicd" which looked OK and comes from sourceforge, so I decided to try it. When I ran Synaptics it said that 'network-manager' would have to be removed, so I went ahead and did all that. Now, the wireless doesn't work at all. "wcid" says 'command not found'. I have no network connection on the T40.

I'd like to just restore network-manager and forget 'wicd' and go back to the old network-manager. So, i've been reading up on 'apt-get' and the '-d' option to download-only.. So I thought I'd try that here on the T60, copy the files over from that apt-get archive file (which I assume is in RAM) to a USB stick and then use the USB on the T40.

Does that sound reasonable?

Then I'll try 'realvz' recommendation.

---

### Post by bliffle on 2007-11-07
Now I can't figure out how to recover the old feisty network-manager, or is it NetworkManager?

Looked in sourceforge. Now I'm looking all over google. If I ever find it I guess I should copy a "...deb" file or maybe a "....gz", prolly both, over to the T40.

I found a "wicd...deb" and a "wificli...tgz" and a"gnome-network-monitor...gz" which I'll prolly try.

Damn. What a nightmare.

---

### Post by bliffle on 2007-11-07
How can I DL the package for NetworkManager to another computer then move it over to the T40 on a pendrive then install it there?

---

### Post by bliffle on 2007-11-08
I figured out how to do an :

```
apt-get -d update network-manager
```

on another computer, copy the resulting .deb out of 

```
/var/cache/apt/archives
```

to a USB stick by doing a :

```
cp /var/cache/apt/archives/net* /media/JUSBDRIVE
```

copy the .deb from the USB :

```
sudo cp /media/JUSBDRIVE/net*  /var/cache/apt/archives/ 
```

and try a standalone install from the T40:

```
sudo apt-get --no-download install network-manager
```

but I got an error msg:

```
E:Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

but I'm not connected on the T40, so I did a 

```
apt-get check network-manager
```

instead. But it didn't report any dependencies for me to resolve.

I'm stumped.

Is there a way I can use the "AlternateCD" as the source of .debs since the T40 is not on the internet?

---

### Post by fictivetoast on 2007-11-13
Try checking out the network-manager-gnome package listing on [http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)

I've gone through this mess before, and have been able to just manually fetch the dependencies one by one on another machine then bring it over.  Each package on the listing will offer files for download at the bottom of the page depending on your architecture.  Try grabbing:

[http://packages.ubuntu.com/feisty/net/network-manager](http://packages.ubuntu.com/feisty/net/network-manager)
[http://packages.ubuntu.com/feisty/net/network-manager-gnome](http://packages.ubuntu.com/feisty/net/network-manager-gnome)
[http://packages.ubuntu.com/feisty/net/wpasupplicant](http://packages.ubuntu.com/feisty/net/wpasupplicant)

Then bring them back over to the netless machine and fire the debs up individually in gnome (starting with wpasupplicant) ; if you need something else, it'll tell you what the dependency is, and you can then shuffle that one over too.

As for the wireless dying though, I've had the same problem on two HP machines and have never found a solid recourse, save rebooting.  :(

---

### Post by bliffle on 2007-11-14
Thanks for the help. I've upgraded from Feisty to Gutsy, and that restored NetworkManager, but I still have the original problem, maybe less often.

---

