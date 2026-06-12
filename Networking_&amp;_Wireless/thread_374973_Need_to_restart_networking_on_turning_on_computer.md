---
title: "Need to restart networking on turning on computer"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-03-03
Everytime that I turn on my computer or boot ubuntu back up I need to run the following code in order to get my wireless connection working (get an IP)
```
sudo /etc/init.d/networking restart

```
I was receiving help with this at [this post]("http://ubuntuforums.org/showthread.php?p=2236152#post2236152") but the url they gave me is a broken link:
[http://www.debianadmin.com/enable-wp...ntu-linux.html](http://www.debianadmin.com/enable-wp...ntu-linux.html)
How can I alleviate this problem?
Also I ran Automatix and some of the programs I chose to install are not anywhere to be found.
Why would this happen?

---

### Post by spd106 on 2007-03-03
Can you post the contents of your /etc/network/interfaces file? (minus any keys, of course)

---

### Post by lsutiger on 2007-03-04
Thanx for the reply!
Here's the contents:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid Tiga
wireless-key 98F6B60C3384565636482252EC

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1

```

---

### Post by spd106 on 2007-03-04
It looks ok. 

Some people have reported similar problems to this in the past. Sometimes it helped to take the interface down, then back up again. 

So perhaps try adding these lines```
auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid Tiga
wireless-key 98F6B60C3384565636482252EC
[COLOR="Red"]post-up ifconfig eth1 down
post-up ifconfig eth1 up[/COLOR]

auto eth2
iface eth2 inet dhcp
```

---

### Post by lsutiger on 2007-03-04
thanx for the reply. Did not work. In fact I had to delete those two lines to make it work.

---

### Post by tetobear on 2007-03-04
> **lsutiger said:**
> Thanx for the reply!
Here's the contents:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid Tiga
wireless-key 98F6B60C3384565636482252EC

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1

```

well how about to use auto instead of iface before eth1
i believe that that is the command that get the interface automatically on on startup...

i use kubuntu 6.10 and int the setting graphic interface there is a flag to do that too...

---

### Post by lsutiger on 2007-03-04
that caused the network not to start...received errors [failed] on boot up. And auto is the last on the list.

---

