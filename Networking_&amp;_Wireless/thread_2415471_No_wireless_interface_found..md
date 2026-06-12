---
title: "No wireless interface found."
date: 2019-03-26
forum: Networking &amp; Wireless
---

### Post by dnivrav on 2019-03-26
Hi! My wifi stopped working out of the blue. The icon doesn't show up. Although, ethernet connection seems to work fine 

When I run the following commands
sudo lshw -c network
It shows no wireless interface

rfkill
indicates only bluetooth and wifi

ifconfig
no wlan 0 module


[IMG]http://www.imageurl.ir/images/48394824329746683804.png[/IMG]



The wireless info can found here: [https://paste.ubuntu.com/p/Xxm5MDFKqf/](https://paste.ubuntu.com/p/Xxm5MDFKqf/)

I have been struggling to find a solution. Any help is appreciated. Thanks

---

### Post by chili555 on 2019-03-26
We see this in your paste:

> [/etc/modprobe.d/rt2800usb.conf]
options rt2800usb ant_sel=1
ant_sel is not an available parameter as you can see from the command:

```
modinfo rt2800usb
```Let's remove the unnecessary file:

```
sudo rm /etc/modprobe.d/rt2800usb.conf
```We see that the driver rt2800usb is loaded because it is declared in the file /etc/modules. Your *lsusb* doesn't show any rt2800usb wireless device. Why did you add that driver to /etc/modules?

We also see faulty entries in /etc/network/interfaces. Let's remove them:

```
sudo nano /etc/network/interfaces
```Now remove the lines you added so that the file now reads:

```
auto lo
iface lo inet loopback

```Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor.

Next, reset the BIOS to defaults, reboot and let us see a new wireless_script result.

---

