---
title: "Bluetooth not working in Intrepid (no device found)"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by bluebook on 2008-11-03
I just installed Intrepid Ibex on my Lenovo x200 (non-tablet), and so far, it has been working beautifully. I just noticed though, that bluetooth doesn't work. While I have the bluetooth icon on my Gnome desktop, I am not able to set any preferences other than about displaying the Bluetooth icon. I've done some searches online and installed bluetooth packages etc. but to no avail.

I think the issue is this: 
sudo hciconfig hci0 reset - returns
> Can't get device info: No such device

grep hcid /var/log/syslog - returns nothing

grep blue /var/log/syslog returns

> Nov  3 09:01:15 doublethink bluetoothd[5705]: Bluetooth daemon
Nov  3 09:01:15 doublethink bluetoothd[5705]: Starting SDP server
Nov  3 09:01:15 doublethink bluetoothd[5705]: Starting experimental netlink support
Nov  3 09:01:15 doublethink bluetoothd[5705]: Failed to find Bluetooth netlink family
Nov  3 09:01:15 doublethink bluetoothd[5705]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Nov  3 09:01:15 doublethink bluetoothd[5705]: bridge pan0 created


Can anyone help? TIA!

---

### Post by Kevbert on 2008-11-03
Do you get anything with ```
hcitool scan
``` Is there a front panel switch that you need to press ?
I know that the developers have been making quite a few changes and there have be reports of bluetooth being broken. I've even raised a bug report on this (the number escapes me).

---

### Post by bluebook on 2008-11-03
hcitool scan -- gives me: 

Device is not available: No such device


there is no switch for bluetooth, only wireless, on my laptop (and that's set to 'on'). It worked fine in Hardy, just before I upgraded (though admittedly, I played with it once).

---

### Post by bluebook on 2008-11-03
hcitool scan -- gives me: 

Device is not available: No such device


there is no switch for bluetooth, only wireless, on my laptop (and that's set to 'on'). It worked fine in Hardy, just before I upgraded (though admittedly, I played with it once).

---

### Post by Kevbert on 2008-11-03
It looks like it's [[COLOR="Red"]this bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/284982") on launchpad. It may be worth you adding a comment.

---

### Post by bluebook on 2008-11-03
Thanks for your help. I went and reported it.

---

### Post by Kevbert on 2008-11-03
You're welcome. The sooner bluetooth is sorted the better. It's not working as well as it used to in Hardy.

---

### Post by john davies on 2008-11-09
HI I am a linux newbie & had some help from a friend to set up my 3 network usb dongle on my webbook after downloading & installing 8.10. 
I upgraded my webbook from 8.04 to 8.10 within a day of getting it but there is a bluetooth logo on F2 but it doesn't seem to  work. It would appear that everybody is having trouble with intrepid & bluetooth anybody out there that has got bluetooth working on webbook with 8.10?
Help would be most appreciated.

---

### Post by soumyamandi on 2009-09-30
I was having the same problem. Now its resolved.It happened that after switching on the bluetooth adapter(same as of wireless) there was another button to activate the bluetooth.So in total there were two switches to be taken care of . In my case latter was function+F5 ..Try finding the latter :)

---

