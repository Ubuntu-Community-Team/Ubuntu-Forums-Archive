---
title: "Noob who needs help"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by nick.huggins on 2007-11-06
I dual booted ubuntu onto my vista laptop and i like it alot there is just one problem.
my pc is a compaq presario c700 and it has a wireless button that lights up blue when it is activated and orange when wifi is activated. when im in ubuntu i cant get the wireless to activate. is there some driver or something i need to install to get my laptops built in wlan to work?:confused:

---

### Post by Lambert on 2007-11-06
> **nick.huggins said:**
> I dual booted ubuntu onto my vista laptop and i like it alot there is just one problem.
my pc is a compaq presario c700 and it has a wireless button that lights up blue when it is activated and orange when wifi is activated. when im in ubuntu i cant get the wireless to activate. is there some driver or something i need to install to get my laptops built in wlan to work?:confused:

Very possible, wireless in linux is a little behind as far as manufacture support and drivers.

The first thing we need to do is identify what your wireless device is.

Open a terminal from the top menu applications -> accesories -> termianl

type in the following and post the output here.

```

sudo lshw -C network

```

And what version of ubuntu did you install?

---

### Post by davidryder on 2007-11-10
> **Lambert said:**
> Very possible, wireless in linux is a little behind as far as manufacture support and drivers.

The first thing we need to do is identify what your wireless device is.

Open a terminal from the top menu applications -> accesories -> termianl

type in the following and post the output here.

```

sudo lshw -C network

```

And what version of ubuntu did you install?

I have the exact same problem and actually the same laptop.  

I have tried using ndiswrapper to install the driver

```

[root@localhost drivers]# ndiswrapper -l
Unknown line at line 2389
bcmwl6 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
[root@localhost drivers]#        

```

One thing that concerns me is the unknown line error - is that important?

Also, I have the button to turn the wi-fi on/off and it's orange (indicating wi-fi is disable) but i don't know if it really has anything to do with enabling wi-fi.  And I can't find anything about whether the button is software or hardware controlled.  

The device (Broadcom BCM94311MCG wlan mini-PCI) shows up in the wireless network window but no networks come up.  When I right click on the network icon in the taskbar and try to switch from eth0 (ethernet) to eth1 (wireless) I am asked for the root password then nothing happens.  After that I go back to active interfaces and eth0 is still checked.

So, I downloaded the drivers from HP (in hopes that it contains a driver for the enable/disable button) and there is chance the driver for the enable/disable button is in the package.  The only thing is I don't know how to go about installing it IF it is the driver for the button.

Ah... I am soooo lost and sooo don't want to go back to vista but if I can't work this problem out that's really my only option...

---

### Post by davidryder on 2007-11-10
I just wanted to announce that Network interface is up on wlan0.  =D>

To save you some trouble I uploaded the drivers I used [here](http://www.phpstory.net/files/bcmwl5.tar.gz)

Here is everything I did:

```

urpmi.update -a

```

To make sure I had the most up-to-date kernel.  Then I experimented with a number of drivers, and while the laptop came with bcmwl6 I found that bcmwl5 is what ultimately worked.

```

ndiswrapper -l

```

bcmwl6 should be listed there and needs to be removed with

```

ndiswrapper -r bcmwl6

```

Now cd into the directory where you have decompressed bcmwl5.tar.gz and install the drivers with the following.  

```

ndiswrapper -i bcmwl5.inf
rmmod ndiswrapper
modprobe ndiswrapper

```

Reboot then you should be able to see the the card with 

```

ifconfig

```

Mine was named wlan0 and you can see a list of networks with

```

iwlist waln0 scan

```

Most of this can probably be done with knetworkmanager.

Post your results!

---

### Post by nick.huggins on 2007-11-29
what do i do if terminal says "no ndiswrapper utils dound!"?:confused:

---

### Post by fjornada on 2007-12-07
at last, a solution that works for my Compaq Presario C742!

thanks for your help, davidryder. I have already tried installing some firmwares, but I couldn't find one that worked! I'd just suggest not using urpmi, since it not the default package manager for ubuntu.

so, for the final user of a Compaq C742 or similar, I'd say the solution is the following:

1) Download bcmwl5.tar.gz (see davidryder's) post. Open a terminal where you downloaded the file and type:
```
tar -xzf bcmwl5.tar.gz
```

2) Type:
```

sudo bash
rmmod bcm43xx
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
apt-get install ndisgtk ndiswrapper-utils-1.9 ndiswrapper-common
ndisgtk

```
That will disable your bcm43xx drivers and install ndiswrapper/user interface


3) Once a window is opened, click on "Install New Driver", go to the directory where you extracted your bcmwl5.tar.gz, go to the subdirectory bcmwl5 and select bcmwl5.inf

After you close the window, your wireless should be working!

--

btw, don't blame Ubuntu if you find this solution difficult. Mandriva 2008 and OpenSuse 10.3 had the same problems.

Tell me if it worked for you too. :)

---

### Post by davidryder on 2007-12-16
> **fjornada said:**
> at last, a solution that works for my Compaq Presario C742!

thanks for your help, davidryder. I have already tried installing some firmwares, but I couldn't find one that worked! I'd just suggest not using urpmi, since it not the default package manager for ubuntu.

so, for the final user of a Compaq C742 or similar, I'd say the solution is the following:

1) Download bcmwl5.tar.gz (see davidryder's) post. Open a terminal where you downloaded the file and type:
```
tar -xzf bcmwl5.tar.gz
```

2) Type:
```

sudo bash
rmmod bcm43xx
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
apt-get install ndisgtk ndiswrapper-utils-1.9 ndiswrapper-common
ndisgtk

```
That will disable your bcm43xx drivers and install ndiswrapper/user interface


3) Once a window is opened, click on "Install New Driver", go to the directory where you extracted your bcmwl5.tar.gz, go to the subdirectory bcmwl5 and select bcmwl5.inf

After you close the window, your wireless should be working!

--

btw, don't blame Ubuntu if you find this solution difficult. Mandriva 2008 and OpenSuse 10.3 had the same problems.

Tell me if it worked for you too. :)

Indeed, I assumed that Ubuntu used the same package manager as Mandriva, as that is what I was gathering that solution from.  I have since wiped my Mandriva installation and installed Ubuntu.  Same exact problem - same exact solution.  fjornada, you solution is better written than mine - thanks for the update!

---

### Post by perroazul on 2008-05-27
hey,
just in case, there is one pretty simple solution based on the use of madwifi package:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html#comment-108680]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html#comment-108680")
it works perfectly with my compaq presario C700 (atheros AR5007 chipset)

---

