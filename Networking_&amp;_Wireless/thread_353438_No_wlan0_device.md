---
title: "No wlan0 device?"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Daz902 on 2007-02-04
Hi there, 

I had a Netgear dongle and as I mentioned in my other post, it caused my laptop to lock up solid after a few minutes. So I went out and bought a  D-Link DWL-G132 WiFi USB dongle. I installed the windows drivers using ndiswrapper and everything seems to be in order if I follow instructions from other forums and pages at least in terms of a successful installation.

The strange thing is that when I plug in the dongle, it doesn't get any powerand Ubuntu doesn't know it's there. 

wlan0 doesn't exist! I don't think this is a driver issue as it seems odd that the device doesn't even get any power when it's plugged in - how could Linux even know it's there? 

I tried plugging in my other Netgear dongle to see if it was a hardware port issue and that results in wlan0 being created. The Netgear one plugs in fine.

What do have to change to ensure that my D-Link dongle is seen when it's plugged in and creates a wlan0?

Thanks,
Darryl

---

### Post by gradedcheese on 2007-02-04
Hi.  Try this.  Remove the dongle, clear you dmesg log:

sudo dmesg -c

now plug in the donge, wait a few seconds, and run:

dmesg

post the output here (there should be something about finding a USB device and doing something with it)

---

