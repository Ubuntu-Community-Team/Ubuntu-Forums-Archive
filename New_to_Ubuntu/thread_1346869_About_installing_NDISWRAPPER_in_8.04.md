---
title: "About installing NDISWRAPPER in 8.04"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-05
Hello Everyone,

I went to System -->Synaptic Package Manager and installed NDISWRAPPER.

Then I went to Synaptic Manager --->  Administration --> Windows Wireless Drivers and installed the Win XP driver for my wireless g device. The driver is said to had been installed but it also show no device present.

So what do I need to do now?

Thank you.

---

### Post by lkraemer on 2009-12-05
What exactly did you install with Synaptic?
I only see ndiskgtk, ndiswrapper-common, and ndiswrapper-utils-1.9
available for install.

If you are going to try and use your Windows Drivers you will need the
INF and SYS files. For example, bcmwl5.inf * bcmwl5.sys are the ones
I have previously used.  Yours will be different according to your
Wifi card manufacturer.  If you have XP available you can go to Control
Panel and locate what the driver is named, then search for it.
Make sure you have the proper 32 bit or 64 bit drivers from the
proper Windows version that matches which Ubuntu (32 or 64 Bit) is installed.

You will also likely have to blacklist some other drivers.
In 8.04 the blacklist file is located at /etc/modprobe.d/blacklist

Post the output of the following Terminal commands:
```

lspci
lsusb
lshw -C network
lsmod
cat /etc/modprobe.d/blacklist
 (OR for => 9.04 use cat/etc/modprobe.d/blacklist.conf)
iwconfig
ndiswrapper -l
dmesg | tail

```
Post the outputs of the above.

If lsmod shows module b43 bcm43xx and others installed you will
need to blacklist them, since you are going to be using ndiswrapper.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```

You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist.

To load the windows driver use these commands:
```

sudo ndiswrapper -i bcmwl5.inf

sudo ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m
cd /etc
sudo gedit modules

```
( and add a new line to the end of the file. Type the following:
ndiswrapper <press enter>)

Now save the file and exit the editor.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

ifconfig
iwconfig
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

lk

---

### Post by suomalainen on 2009-12-06
Is any of this dependant upon chipset of the NIC being used?

What I did as a fix was to swap out cards and now I'm up and running.

---

### Post by lkraemer on 2009-12-07
Is any of this dependant upon chipset of the NIC being used?

YES, it certainly is........

And that is one way to fix the problem.

The first tree commands would have helped identify the installed Wifi Card.

lk

---

