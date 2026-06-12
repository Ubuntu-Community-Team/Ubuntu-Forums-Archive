---
title: "Cannot Activate Ralink RT2500 Wifi Card"
date: 2005-11-01
forum: Networking &amp; Wireless
---

### Post by Plank117 on 2005-11-01
I've upgraded to breezy, upgraded my kernel to k7, and figured out how to configure powernowd. I've got a fairly viable linux laptop, suitable for working on assignments out on campus. My school is going to have WiFi installed before the end of the year, and I enjoy the freedom of having a computer with all of my stuff on it that I can take on campus, rather than use the crappy PCs they bought off a gypsie 32 years ago. In theory, my wireless card should work with breezy right out of the box. However, this is not the case, so does anyone have any ideas or good tutorials they know of?

---

### Post by mips on 2005-11-01
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

---

### Post by Plank117 on 2005-11-01
I've seen that tutorial before, and it says that it's irrelevant to anyone using breezy. Will this work?

---

### Post by frenkel on 2005-11-01
After the install of Breezy, the rt2500 module should be installed and loaded automatically, and there should be a ethernet device called ra0. You can then configure it with the System->Administration->Networking tool.
At my computer it works great!

---

### Post by Plank117 on 2005-11-01
Ok, I listed my network devices with ifconfig, and ra0 does not show up anywhere. Also, the Makefile in the RT2500 driver I downloaded appears to be broken. Whenever I run "make" I get the following output:
```

make[1]: Entering directory `/lib/modules/2.6.12-9-k7/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-k7/build'
rt2500.ko failed to build!
make: *** [module] Error 1

```
I made a /build directory in there because I thought that was the problem, but I guess not. There were some instructions that came with the driver that stated that I needed to make some symbolic links in this particular directory, but the tutorial on the Wiki didn't mention this step.

---

### Post by Plank117 on 2005-11-01
I took a look at the README file that came with the driver, I'm going to try those instructions. I will post my findings. <EDIT: I took a look at these instructions (listed below) and they are identical to those found in the wiki. Have I extracted the archive in the wrong place?>
```

Installation instructions for the rt2500 Module

=======================================================================
Build Instructions:  
====================
For 2.4 or 2.6 series kernel:
a. $tar -xvzf rt2500-x.x.x.tar.gz
    go to "./rt2500-x.x.x/Module" directory.

b. $make                # compile driver source code

c. $make install	# installs kernel module driver 

```

---

### Post by frenkel on 2005-11-02
It's already installed, run a

$ sudo modprobe rt2500

and the ra0 interface should be up.
To compile the module, you need to install the kernel sources (not installed by default), but as I said, there is no need to compile them, just run sudo modprobe rt2500.

Good luck,
Frank

---

### Post by Plank117 on 2005-11-02
Eh, no. I don't get any output when I run this command.

---

### Post by frenkel on 2005-11-02
[QUOTE=Plank117]Eh, no. I don't get any output when I run this command.[/QUOTE]
I didn't say you would get any output. No output means the module is now loaded. Now you can check if the interface is there by running:
$ ifconfig
If it's there, you can configure it with System->Administration->Networking...

---

### Post by Plank117 on 2005-11-02
Yeah, I just realized that. I looked at the man page and found it by listing out everything containing "rt2500."
```
modprobe -l rt2500
```
My god, I might get this working before I go to school...

---

### Post by blazko on 2005-11-14
Rehi,

Wow! Ralink cam w/ Breezy! That is nice!
However, I fail to activate it. The device is liste unconfigured using iwconfig, but as soon as I want to configure the tool with network-admin and click on activate (in order to beable to enter values at all), the entire system freezes, I cannot kill X, just the mouse still moves and the power button fires events, the rest nada.

Before I do play around with /etc/network/interfaces, ifup, ifdown and the like, I would like to ask if someone had similar probs and got it working.
I am not able to get debugging info as nor /var/log/messages gets that far and when running network-admin from a console, it also does not come so far to tell me anyhthing... :-(

Important note: I run Breezy as 64bit version on an AMD64 3800+.

Thanks and greetings, Timo

---

