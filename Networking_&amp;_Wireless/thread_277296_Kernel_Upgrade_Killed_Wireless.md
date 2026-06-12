---
title: "Kernel Upgrade Killed Wireless"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by mrunion on 2006-10-14
I upgraded my kernel thhis am from 2.6.15.23 (386) to 2.6.25.27 (686 + SMP).  Now the wireless access doesn't work.

If I boot the old kernel all I haveto do is press the little wireless button on the laptop and the WiFi light comes on and I'm good.

If I boot back to the latest kernel, the button doesn't make the light come on and WiFi doesn't work.

I tried various "sudo ndiswrapper ..." commands and got no where.  BOTH kernel versions show "no drivers" are installed when using ndiswrapper -l.

The machine is an HP dv8000.  Again, it works FINE with the older kernel.  I'm just no adept enough at this Linux stuff to know what's missing.

I've searched for an hour and cannot find anything that helps.  Can someone tell me what to look at?  Like I say -- I *know* it works, I just want it to work with the latest kernel.

---

### Post by mrunion on 2006-10-14
Since this troubleshooting thing is being difficult, I ran both versions of the Kernel again.  here is the funny stuff:

2.6.25.23-686:
sudo ndiswrapper -l  #Gives "no drivers loaded, yet I can get on the internet
lsmod gives a list of 100 things, and ndiswrapper IS NOT one of them

2.6.15.27-686 (SMP):
sudo ndiswrapper -l  "Gives "no drivers loaded, but I CANNOT get on the net
lsmod gives a list of 100 things, ndiswrapper is not one of them AND the list is IDENTICAL to the .23 version!!

Aaarrrggghhh!  What gives?  I suspect that the problem is with the HARDWARE BUTTON that does not turn on in the .27 kernel.  But I have NO idea how to go further into this.

Does anyone have any clues?  What log files should I look at?  Anything?

---

### Post by dbott67 on 2006-10-14
When you got wireless working with the .23 kernel, did it "just work" or did you have to install the latest version of ndiswrapper or do any other voodoo to make it work?

In my case, I had to download & compile the latest version of ndiswrapper from here [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) and followed these instructions to install it [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

I created [this thread]("http://www.ubuntuforums.org/showpost.php?p=1601702&postcount=1") a few days ago outlining my steps (in case I ever have to do it again).  You need to install 'build-essential' from Synaptic to compile ndiswrapper.

-Dave

---

### Post by nikarul on 2006-10-14
I'm using the ipw3945 driver on my hp laptop.  It works in 2.6.15-26 but broke when I upgraded to 2.6.15-27.  Switching back to -26 fixes it.  I didn't have to do anything special to get it to work with -26.

---

### Post by dbott67 on 2006-10-14
Hi Matt,

I'm confused... are you sure you're using ndiswrapper?  If **ndiswrapper -l** returns 'no drivers loaded' then I would assume that the kernel has native support (at least the old kernel does).

Run the following command while in the ***old kernel*** to find out the name of the wireless driver:
```
lsmod | grep ipw
```
*(this should return all modules that have **ipw** in their name)*

Let's assume the module is called '**ipw3945**'.  You could try loading the drivers manually:
```
sudo modprobe ipw3945
```
```
sudo /etc/init.d/networking restart
```

You can also try the following commands to deactivate & activate the wireless interface:

```
sudo ifdown wlan0
```
```
sudo ifup wlan0
```

Note: your wireless card may mot be wlan0.  Type **ifconfig -a** from the old kernel to determine the interface name.

-Dave

---

### Post by mrunion on 2006-10-17
Thanks guys.  Sorry for the delay in responding.  I actuall just removed the "27" version and will stay with "23" for the time being.

I actually think the problem is related to the "restricted modules".  I don't know this but that seems to be the thing.  I will definitely work with this a bit later on when I have a little more time.  There is a few mor pressing things than the kernel right now (not Linux related stuff).

Anyway, thanks for the assistance and I will definitely return and follow through this thread when I attempt to upgrade again.

---

