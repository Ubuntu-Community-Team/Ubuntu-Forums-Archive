---
title: "Scanning for wireless networks manually."
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by JesterDev on 2008-06-09
I have been having a hard time searching for wireless networks. In particular I am having a hard time connecting any network that does not have security. So anyway I am wondering how I might scan for networks manually in the console-I'm hoping that my network manager will pick on them also. This seemed to help with OpenSuse, I'm hoping the same goes here.

---

### Post by issih on 2008-06-09
Not sure it will really help you much, but the following are the commands you want to look at:
```
iwlist scan
```
will list any detected networks.

As you say you have no encryption,
```
sudo iwconfig essid <your networks ssid>
```
will connect to your access point,

now work out what your wireless interfaces logical name is by running:
```
iwconfig
```
It will be something like wlan0 or eth1, hopefully it will be obvious.

Finally acquire a network address by dhcp using:
```
sudo dhclient <logical name>
```
You should now be connected to the internet!

---

### Post by JesterDev on 2008-06-09
Thank you! I will try that out next time I am at work. I have a secure connection at home and have no issues at all. But the work connection is not secure (although I have suggested they change that) and I always have a hard time connecting.

---

### Post by vjones777 on 2008-06-10
You may also want to try SWScanner - it's a nice gui app.  The only issue I had with it is that I had to run it as root for it to work properly, though that may have just been me.

A minor issue is that the SNR is always incorrectly reported as zero.  It's a KDE app but runs under gnome ok if you dont mind running KDE apps.

I think I got it from the repositories - I don't recall which I'm afraid.

---

