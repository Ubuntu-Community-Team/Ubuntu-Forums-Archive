---
title: "Inspiron E1705 Wireless Problem"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by dpek on 2011-06-28
Hello all, I've been having a problem with setting up the wireless connection on my old Inspiron E1705. Being completely new to Ubuntu, I spent quite a while looking for solutions, but none of them have worked. If you can help, that would be great :)
[U]
[SIZE=2]Here's some information that might be useful:[/SIZE][/U]
OS: Ubuntu 11.04
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
In Administration>Additional Drivers, the Broadcom STA wireless driver is installed.
When trying to connect to a network by clicking on the network icon in the top panel, only the ethernet option is available even though wireless is configured.
Contents of my etc/network/interfaces file:
> auto lo
iface lo inet loopback
The bios reports that the Wireless and Bluetooth are enabled, along with the ethernet.
The wifi led on my laptop is off; pressing FN+F2(The wireless key) doesn't do anything.

---

### Post by wolfen69 on 2011-06-28
Go to additional drivers and remove the driver. Then open a terminal and do:
```
sudo apt-get install b43-fwcutter
```
let us know how it goes.

---

### Post by dpek on 2011-06-28
> **wolfen69 said:**
> Go to additional drivers and remove the driver. Then open a terminal and do:
```
sudo apt-get install b43-fwcutter
```let us know how it goes.
That didn't seem to do anything.

---

### Post by dpek on 2011-06-29
Bump. (I hope I'm allowed to do that.)

---

### Post by fractalman on 2011-06-29
best to only bump once in a 24 hr period,

you might find something in these if you haven't looked already

[http://ubuntuforums.org/showthread.php?t=883271](http://ubuntuforums.org/showthread.php?t=883271)

[http://ubuntuforums.org/showthread.php?t=1390535](http://ubuntuforums.org/showthread.php?t=1390535)

or for linux wireless drivers

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

i think as yours is BCM4311 802.11b/g, the 802.11  means you will need the  b43legacy driver, i'm not an expert so i can't say 100% if this is the case but there's no harm in trying,

hope this helps :-)

---

### Post by bkratz on 2011-06-29
> **fractalman said:**
> best to only bump once in a 24 hr period,

you might find something in these if you haven't looked already

[http://ubuntuforums.org/showthread.php?t=883271](http://ubuntuforums.org/showthread.php?t=883271)

[http://ubuntuforums.org/showthread.php?t=1390535](http://ubuntuforums.org/showthread.php?t=1390535)

or for linux wireless drivers

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

i think as yours is BCM4311 802.11b/g, the 802.11  means you will need the  b43legacy driver, i'm not an expert so i can't say 100% if this is the case but there's no harm in trying,

hope this helps :-)


Actually the b43 driver is correct, not the b43legacy.  this post will work.

[http://ubuntuforums.org/showpost.php?p=10758325&postcount=25](http://ubuntuforums.org/showpost.php?p=10758325&postcount=25)

---

### Post by fractalman on 2011-06-30
Ok, thanks, like i said i'm not an expert, i just found that on the linux drivers page and thought it might help  :D

---

