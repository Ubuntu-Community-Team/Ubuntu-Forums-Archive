---
title: "Wifi flaky on macbook air broadcom4360"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by ELD on 2014-12-31
Sadly the broadcom driver from drivers manager on ubuntu keeps my wifi on, but it seems to drop out every few minutes, sometimes making me having to press enter on an url multiple times, dropping me from irc etc.

My wireless info script paste:
[http://paste.ubuntu.com/9651428/](http://paste.ubuntu.com/9651428/)

---

### Post by Hadaka on 2014-12-31
Hi, that is a rare wifi card so, may not be much that can be done.
you have some known entrys that may be causing you problems.
```
BTHub5-SQWM          : ssid=BTHub5-SQWM | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto
  BTHub5-SQWM 1        : ssid=BTHub5-SQWM | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 
```
the ...space.....1 should be deleted or changed to different name,
in your router settings TKIP is current that should be changed to WPA2
and in network manager your IPv6 should be set to ignore.
try those changes, and report back.
thanks.

---

### Post by ELD on 2015-01-11
The "space 1" really won't cause an issue, it just the network name used by a USB network adapter.

I have set ipv6 to ignore, and removed the other stored network name used by the usb adapter as I'm not using it now.

What else can I do? Is there a way to test how good/bad the chip is?

---

