---
title: "wifi reconfure at boot"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by sanone on 2007-01-17
I'm using ubuntu 6.10 and have this annoying problem for quite a while now and I was hoping that someone could help me out here.

In my notebook I have a wifi card which does work out of the box which is nice.. but there every once in a while, it is kinda random, I have to reconfigure my network settings. 

For some unknown reason I have to do the following steps.
1. Goto System -> Administration -> Network.
2. Disable my wired connection.
3. Enable and setup, specify ESSID etc., for my wireless connection.

The weird thing here is that I _never_ use the wired connection and use my notebook always with the same wireless router.

Perhaps there is a simple solution but I haven't found it.

Cheers,
San

---

### Post by infol on 2007-01-17
hi san!

can you post the contents of /etc/network/interfaces ?

---

### Post by sanone on 2007-01-17
Sure!

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth2 inet dhcp

iface eth3 inet dhcp
wireless-essid sanenbabs

auto eth3

```

---

### Post by infol on 2007-01-17
if you never use anything but your wireless card, i'd try deleting all interfaces (or commenting out) in /etc/network/interfaces except lo and wlan0, i.e. leaving it with only

```
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
wireless-essid sanenbabset dhcp

```

and then

```
sudo /etc/init.d/networking restart
```

to see if it works..

---

### Post by sanone on 2007-01-18
Thanks for the reply but I find it kinda hackerish.. is there not a more professional solution for this problem? Or do you have an idea why this happens?

---

### Post by akajonesy on 2007-01-18
I have been having a similar problem, wireless network settings disappearing on reboots.
Started a post, but still no solution. (Reenter everything in terminal in order to log on).

Seems to me that Ubuntu is registering the device as a wired connection (eth1 in my case) as opposed to a wireless (wlan0) connection.
No idea how to reconfigure it though. :(

---

### Post by sanone on 2007-01-21
Perhaps we should write a bug report... because this is something that should be fixed for 7.04 imho.

---

### Post by akajonesy on 2007-01-22
installing Network-administrator from synaptic seems to have done the trick
No idea why though.

---

### Post by sanone on 2007-01-27
> **akajonesy said:**
> installing Network-administrator from synaptic seems to have done the trick
No idea why though.

I assume you mean network-manager? And that didn't do the trick here...

---

### Post by haiku99 on 2007-01-27
> **sanone said:**
> I assume you mean network-manager? And that didn't do the trick here...

it looks like maybe Ubuntu is assigning different ID"s to your wireless card at times, i.e. wlan0, eth2, eth3 ....there is a way to pin the ID's to the mac addresses of the interface cards but don't remember the specifics, something to do with the /etc/iftab file, a forum search should find it.  Once that is done you can edit the /etc/network/interfaces file to show only the correct connections, this IS a professional way to do it and is not "hackerish", though I would not delete the eth0 wired connection....if you are experimenting you can comment out a line by putting a # before it.

---

### Post by sanone on 2007-02-05
> **haiku99 said:**
> it looks like maybe Ubuntu is assigning different ID"s to your wireless card at times, i.e. wlan0, eth2, eth3 ....there is a way to pin the ID's to the mac addresses of the interface cards but don't remember the specifics, something to do with the /etc/iftab file, a forum search should find it.  Once that is done you can edit the /etc/network/interfaces file to show only the correct connections, this IS a professional way to do it and is not "hackerish", though I would not delete the eth0 wired connection....if you are experimenting you can comment out a line by putting a # before it.

That was indeed the case... I installed Ubuntu on another machine (I have no cd/dvd drive in this notebook) and switched harddrives after installation... No I have no problems anymore and Ubuntu can't really be blamed for missing this. On the other side it would be nice if Ubuntu detected that the mac addresses weren't availible on this machine and some others were.

Anyways thanks for the help!
San

---

