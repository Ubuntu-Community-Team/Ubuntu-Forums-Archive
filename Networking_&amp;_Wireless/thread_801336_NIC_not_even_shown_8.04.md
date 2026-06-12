---
title: "NIC not even shown 8.04"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by gionnico on 2008-05-20
I've just installed 8.04 64-bit.

Just after a computer, with a P5K SE motherboard.

Now, lspci doesn't even show me the "ethernet" card. Nor gnome does of course.

I've tried modprobe atl1 but it didn't help!


What can I do??!

---

### Post by mapes12 on 2008-05-20
Did you have a previous version of Ubuntu on your machine before 8.04 and if so did your ethernet card initialise?

Does

```
sudo lshw
```

show anything under *-network  ?

---

### Post by gionnico on 2008-05-23
> **mapes12 said:**
> Did you have a previous version of Ubuntu on your machine before 8.04 and if so did your ethernet card initialise?

Does

```
sudo lshw
```

show anything under *-network  ?

No, it's a new computer.

And no, I can't see any *-network.

---

### Post by mapes12 on 2008-05-23
What do you get from a ping request:

```
ping -c4 127.0.0.1
```

---

### Post by gionnico on 2008-05-25
Network unreachable.

Please help: do I need to load the correct kernel driver or lshw should show the NIC anyways??

---

### Post by mapes12 on 2008-05-25
lshw will show everything Ubuntu detected at install. From what you have posted there are 2 possibilites:

1. You have faulty hardware - Try another unmentionable OS and see if the NIC is detected. If not, kit back to vendor.

2. Slip in another NIC PCI card that IS supported in Ubuntu. See here:

[http://ubuntuforums.org/showthread.php?t=361236](http://ubuntuforums.org/showthread.php?t=361236)

:guitar:

---

