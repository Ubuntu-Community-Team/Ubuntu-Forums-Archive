---
title: "Very slow Ethernet connection"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by aryangor on 2010-08-02
I have a desktop and a laptop at my office. Both have Lucid on them and both are up to date. Internet provider is the same on both machines, yet my laptop network speed is 10X slower than that of my desktop. I tested both machines via [www.speedtest.net](www.speedtest.net).

Since we use proxy and DHCP at work, I use the same network cable for both PC's, plugging the one that needs network, one at a time. Both machines have the same MAC address - could this (spoofing) have caused the problem?

I have struggled with this for over a month, searched here but found no similar post, posted already and got no reply. Please, can someone help me?

Thanks!!

---

### Post by aryangor on 2010-08-02
Maybe I found something that can lead to the right direction.

Installed lshw-gtk on my laptop:
```
sudo apt-get install lshw-gtk && sudo lshw-gtk
```

Then I went to compare the ethernet configurations between both PC's and I found this:

**DESKTOP:**
```
size: 100MB/s
capacity: 1GB/s
width: 64 bits
capabilities:
	10MB/s,
	10MB/s (full duplex),
	100MB/s,
	100MB/s (full duplex),
	1GB/s,
	1GB/s (full duplex),
configuration:
	duplex: full
	speed: 100MB/s

```

**LAPTOP**
```
size: 10MB/s
capacity: 100MB/s
width: 32 bits
capabilities:
	10MB/s,
	10MB/s (full duplex),
	100MB/s,
	100MB/s (full duplex),
configuration:
	duplex: half
	speed: 10MB/s

```

There are definite differences here. Can it be the reason why my speeds are 10X slower? Also, what is "duplex" and is there a way to change it?

---

### Post by tarps87 on 2010-08-02
Short answer is half duplex sends messages in one direction at a time, duplex uses half the cable for each direction. The speed difference could well be due to the network connection, however the size may depend on your ISP. Are both computers connected to the same switch/device?

---

### Post by mastablasta on 2010-08-02
laptop seems to have a weaker card. 
 
also my laptop sometimes for no good reason changes max speed to 10 MB/s instead of 100MB/s. i forgot when this happens, but i think it depended on weather it booted with battery or power cord. not sure though... had this happen to me in windows as well.

---

### Post by aryangor on 2010-08-03
**@tarps87:** Thanks, now I know what duplex is. As I mentioned, there is only one network cable in my office, so I either connect my desktop or my laptop - expecting identical performance from both.

**@mastablasta:** Size and Capacity of the two network cards has 10x difference. How about trying to change the speed parameter/setting - how can that be done? Unless this will work, you might be right and there are hardware limitations. :(

---

### Post by tarps87 on 2010-08-03
So you did, this may help:
```
sudo apt-get install ethtool
sudo ethtool -s eth0 speed 100 duplex full

```
I am currently having difficulties getting this to change the setting and haven't much time to look at it currently. It is worth a try though.

---

### Post by aryangor on 2010-08-03
> **tarps87 said:**
> So you did, this may help:
```
sudo apt-get install ethtool
sudo ethtool -s eth0 speed 100 duplex full

```
I am currently having difficulties getting this to change the setting and haven't much time to look at it currently. It is worth a try though.

Hmmmm.... thanks for that! I executed the code and this is what **lshw-gtk** shows:

```
configuration:
	duplex: full
	speed: 100MB/s
```

... and yet... the speed is FAR below 100MB/s ;( I guess there is nothing else that can be done except to accept the hardware limitation. (sigh)

Thanks everyone!

---

### Post by tarps87 on 2010-08-03
As that has set it, to make the fix persist you need to add this to the end on the /etc/network/interfaces file:

pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full autoneg off

It should look something like this

auto eth0
iface eth0 inet dhcp
pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full autoneg off

As for why it is still running at a slower speed, yes it does seem like a hardware limitation.

---

