---
title: "Driver not working for Realtek Gigabit LAN card"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by Tag_yer_dead on 2007-02-18
hey guys
I have been searching for a linux driver for my Realetk Gigabit Lan (on motherboard).  I tried the r8169 driver but couldnt seem to find something that worked (maybe outdated?).

If you have ne ideas please get back to me with one, cause im stumped....

---

### Post by Reedbeta on 2007-02-18
Have you tried using ndiswrapper?  It's designed for wireless cards primarily but might also work for your wired network card.  See [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and [here](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L) for specific directions.

---

### Post by Tag_yer_dead on 2007-02-19
thanks for the tip but it did not work....
the card is detected, and worked on the LIVE cd, but doesnt work on the partition

---

### Post by gradedcheese on 2007-02-19
you definitely don't want/need ndiswrapper here, this card is supported.  especially if it worked on the Live CD.  I assume the interface is eth0, right?  Does it exist?

```

ifconfig eth0

```

can you bring it up?

```

sudo ifconfig eth0 up

```

and, if you use DHCP, as for an address?

```

sudo dhclient eth0

```

now, try and ping something on your LAN (like your router) -- does that work?  If you can ping on the LAN but can't get online, chances are it's a DNS problem.  Sometimes, if this all doesn't work, you can get somewhere by reloading the driver and then bringing the interface up.  Assuming the driver name is "r8169" (you can check by looking at the output of "lsmod"), you could try:

```

sudo ifconfig eth0 down
sudo rmmod r8169
sudo modprobe r8169
sudo ifconfig eth0 up

```

---

### Post by Tag_yer_dead on 2007-02-19
thank you very much that worked very well for me.

---

