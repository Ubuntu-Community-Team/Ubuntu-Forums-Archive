---
title: "Problem with Intel pro/wireless 3945bg"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by dorian06 on 2008-05-27
I use ubuntu hardy heron and I'm trying to run my card wireless card
(Intel pro/wireless 3945bg). I install the ipw3945 drivers
and now It says its enable but no working, like this:

[IMG]http://img.godlike.cl/images/1gih.jpg[/IMG]

and in my network settings it doesn't appears.. 

[IMG]http://img.godlike.cl/images/2rkb.jpg[/IMG]

I don't what to do...
thx for any help.

---

### Post by dorian06 on 2008-05-27
Ok...I found the solution....


There are a few different problems that could be causeing this, but one thing that may help you is to remove the entry in your udev rules that refers to your wireless card. It sounds scary, but it's really no biggie. Fire up a terminal and run
Code:

sudo gedit /etc/udev/rules.d/70-persistent-net.rules

And then find the line that refers to your wireless card. It will look something like this:
Code:

# PCI device 0x14e4:0x1713 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:a0:fd:19:af", NAME="wlan0"

Your memory offsets and MAC addresses will be different, but the main thing you're looking for is the wlan0 and the ipw3945 (this might say iwl3945 instead). Remove (or comment out if removal make you nervous) these lines, save and reboot. Hopefully you'll be in business.

---

### Post by macogw on 2008-05-28
> **dorian06 said:**
> Ok...I found the solution....


There are a few different problems that could be causeing this, but one thing that may help you is to remove the entry in your udev rules that refers to your wireless card. It sounds scary, but it's really no biggie. Fire up a terminal and run
Code:

sudo gedit /etc/udev/rules.d/70-persistent-net.rules

And then find the line that refers to your wireless card. It will look something like this:
Code:

# PCI device 0x14e4:0x1713 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:a0:fd:19:af", NAME="wlan0"

Your memory offsets and MAC addresses will be different, but the main thing you're looking for is the wlan0 and the ipw3945 (this might say iwl3945 instead). Remove (or comment out if removal make you nervous) these lines, save and reboot. Hopefully you'll be in business.

iwl3945 is the current driver.  It should work automatically in Hardy. ipw3945 is for Gutsy and older only.  Those rules shouldn't have been there in Hardy, though I suppose forcibly installing the wrong driver could do it.  The presence of those rules was a bug known early in development as a problem with upgrading from ipw3945 to iwl3945, but it was fixed partway through.

---

