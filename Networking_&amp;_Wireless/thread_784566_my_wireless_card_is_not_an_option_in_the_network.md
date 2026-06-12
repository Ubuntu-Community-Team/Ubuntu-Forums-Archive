---
title: "my wireless card is not an option in the network"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by cwrann on 2008-05-06
I recently put a fresh install of gutsy back on my computer (hardy wasn't working). After loading the ndiswrapper and firmware onto my computer my wireless card is no longer an option in network. It was there before I put the ndiswrapper and firmware on.

I have no other way to connect the laptop to the internet other than wireless card. (no ethernet port, no phone jack)

My wireless card is listed in lspci.

---

### Post by cwrann on 2008-05-06
I tried sudo ifdown eth 1 and got the response that the interface is not configured. How do I configure the interface?

---

### Post by Ayuthia on 2008-05-06
> **cwrann said:**
> I tried sudo ifdown eth 1 and got the response that the interface is not configured. How do I configure the interface?

What happens when you do a sudo modprobe ndiswrapper (check dmesg)?  Also what is your wireless card (lspci -nn)?

---

### Post by cwrann on 2008-05-06
nothing happens when I modprobe ndwrapper. Not sure how to check dmesg.
My wireless card is a Broadcom corporation BCM 4318 [airforce on 54g] etc.

It used to work on this computer with this distro.

---

### Post by Ayuthia on 2008-05-06
You can just run dmesg in the Terminal and it will list out lots of messages about various things going on in the operating system.

Also from the terminal, have you check lshw -C network to see what your wireless is trying to use?  It might be that bcm43xx is not blacklisted.

---

### Post by cwrann on 2008-05-06
What should I be looking for in dmesg. One thing it tells me is that "ndiswrapper version 1.45 loaded (smp=yes)"

When I "lshw -C network" one of the things it tells me is that the "network is unclaimed" It also lists the specs of my wireless card. What should I be looking for here?

---

### Post by Ayuthia on 2008-05-06
lshw -C network should look like this:
```
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:73:32:fc:24
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,07/11/2007, 4.150. ip=192.168.1.101 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```
Look at the configuration line.  The driver should show ndiswrapper.

As for dmesg, we are just looking for error messages for ndiswrapper.  The error messages should be somewhat obvious, I think.

We can also check:
```
lsmod |grep -i -e bcm43xx -e ndiswrapper
```This will tell us if any modules are loaded.  This will return nothing if the modules are not loaded.
```
cat /etc/modprobe.d/blacklist |grep -i -e bcm43xx -e ndiswrapper 
```This will see if either one of them are blacklisted.  If nothing comes up, nothing is blacklisted.
```
ndiswrapper -l
```
Just to see which driver is loaded into ndiswrapper
```
ndiswrapper -v
```
Just to verify that it does not reply saying that a version is too old or something is missing.

---

### Post by cwrann on 2008-05-06
lshw -C network is similar to yours except that the first line is *network UNCLAIMED and the description is "network controller". I have no capabilities or configuration lines at the bottom.


Heres what I get from
```
lsmod |grep -i -e bcm43xx -e ndiswrapper
```

```
ndiswrapper    185240  0
usbcore              138632   3 ndiswrapper,uhci_hcd
```

Nothing is returned with:
```
cat /etc/modprobe.d/blacklist |grep -i -e bcm43xx -e ndiswrapper
```

ndiswrapper -l tells me that ndiswrapper is not installed but I have installed it. when I
```
apt-get install ndiswrapper-common
```

it tells me that I need to insert the Hard heron disk that I had tried to upgrade with but that didn't work.

---

### Post by cwrann on 2008-05-06
For some reason Hardy Heron was still checked in software sources. I unchecked it I then reinserted my Gutsy disk and did  apt-cdrom add and aptitude update. I then did apt-get install ndiswrapper-common. Now ndiswrapper -l gives me

```
Error: no ndiswrapper utils found!
```

---

### Post by cwrann on 2008-05-06
I reinstalled ndiswrapper and did ndiswrapper- l and now it is telling me 
```
bcmwl5 : invalid driver!
```

---

### Post by cwrann on 2008-05-06
I installed the driver that came with the card. (it was a minor miracle that I found the install cd). Now everything is working great, I guess I just got a bad generic driver.

Thank you for your help.

---

### Post by Ayuthia on 2008-05-06
> **cwrann said:**
> I reinstalled ndiswrapper and did ndiswrapper- l and now it is telling me 
```
bcmwl5 : invalid driver!
```
I am guessing that you figured out that you needed ndiswrapper-common and ndiswrapper-utils-1.9.  You might need to remove the driver and install it again.  Not for sure if you recall how to remove a driver or not:
```
sudo ndiswrapper -e bcmwl5
```

EDIT:
I guess you did know!!!  I missed the last post...  Glad to see it working!!

---

