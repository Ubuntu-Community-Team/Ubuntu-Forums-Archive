---
title: "Need to turn interface off and on again. Why?"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by x64Jimbo on 2007-02-26
Hey folks, I have a Broadcom BCM4311 card working just fine under ndiswrapper except for one point: Whenever I boot up, I have to use the little "wireless on/off" button to turn the interface off and then on again before the interface will get an IP address. It shows up in ifconfig and in NetworkManager. It even scans networks and tries to join them. But until I turn it off and on again, no luck. When resuming from hibernate, if it has been reset before, this doesn't happen, so I assume it's something goofy with ndiswrapper right after it's been modprobed on boot, but before it's been connected. Anyone have any ideas?:confused:

---

### Post by x64Jimbo on 2007-02-28
Bump
Anyone?

---

### Post by Floppyjoe on 2007-02-28
I looked through this wiki thread:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)
And I think your device may not automatically get started on boot if you don't have the ifup, ifdown commands in your /etc/network/interfaces file. There is a reference to this problem in section 8 (no pun intended) of this guide.
I think this problem is specific to this device.

Floppyjoe

---

### Post by x64Jimbo on 2007-02-28
You might be right, but the wiki entry you listed does not have instructions about how to add the ifup and ifdown commands to the /etc/network/interfaces file.

---

### Post by Floppyjoe on 2007-02-28
Maybe add the following to your /etc/network/interfaces file by:
```
sudo gedit /etc/network/interfaces
```
Then add the following
```
ifdown wlan0
ifup wlan0
```
I don't know if that will work but it probably will.

---

### Post by x64Jimbo on 2007-03-01
> **Floppyjoe said:**
> Maybe add the following to your /etc/network/interfaces file by:
```
sudo gedit /etc/network/interfaces
```Then add the following
```
ifdown wlan0
ifup wlan0
```I don't know if that will work but it probably will.
The /etc/network/interfaces file is not a script. It's a configuration file.

---

### Post by Floppyjoe on 2007-03-01
Well I don't know much about scripts but maybe you can make one that does this for you at boot up.

---

### Post by x64Jimbo on 2007-03-01
> **Floppyjoe said:**
> Well I don't know much about scripts but maybe you can make one that does this for you at boot up.
That's a good point. Maybe I'll stick it in an init script.

---

