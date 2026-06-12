---
title: "Eth0 doesn't activate at startup"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by hanexar on 2007-01-13
Hi,

For some unknown reason, my eth0 device doesn't load anymore on startup. I need to go in networking and activate it everytime. It's not a major problems but quite anoying, considerating it was working fine before.

I check the /etc/network/interfaces files, and it is still there: 

```

auto eth0
iface eth0 inet static
```

Any idea how I could get it back working on startup?

Thanx

---

### Post by rocknrolf77 on 2007-01-13
Ran in to the same problem too once. Don't know why it happens, just hope someone can figure it out. Good to know how to fix it if it happens again. :)

---

### Post by hanexar on 2007-01-13
hmm... Does that mean that I can hope for the situation to come back to normal for no reason? I hate unpredictable science! ](*,)  ](*,)  ](*,)

---

### Post by raspi on 2007-01-13
Did you use static IP in the past or DHCP?

---

### Post by hanexar on 2007-01-14
static, didn't change those setting.

This problem came up when I log on while the ethernet cable was unplugged. Ever since after I needed to active the device.

---

### Post by hristo.doynov on 2007-02-08
Exactly the same situation here with me. 

Both my interfaces used to work perfectly (lo and eth0 - 100Mbit wired ethernet adapter), although I had another problem with samba auto-mount no startup. I didn't use the Ubuntu for a while (it's dual-boot with Win2K) and today it simply does not activate both interfaces on startup. After force restart of the network (sudo ifup -a --force) both of them work just fine... The most irritating thing is that there is a coleague if mine 3 desks away that had the same problem with Ubuntu Server and he resolved it (or it resolved itself) and he can't tell me how...

Please help, as while not crucial to the functionality of mu workstation, it is realy pisses me off...

Best regards and thanks in advance, Hristo.

---

### Post by hristo.doynov on 2007-02-08
Hi, hanexar. 

I seem to have solved the problem. :) 

Dunno if it will work for you, as the problem seem to have originated (I think) by a size problem with my /var during an upgrade to 6.10 and the actions I took to solve it. I created a new partition, formatted it and copied the content of the original /var into it, N.B.: using copy -a. This seem to have copied the /var/run and/or /var/lock with wrong permisions/content/whatever else that can be screwed by copy of a system file. 

A Google search led me to this problem and the first reply (by Jeff Waugh) held the solution for me:

[http://lists.slug.org.au/archives/slug/2006/08/msg00318.html]("http://lists.slug.org.au/archives/slug/2006/08/msg00318.html")

The command batch issued an error message about one of the folders in quiestion already existing, but after the reboot both my interfaces (lo, eth0) were up and running.

I sencerely hope this will be of any help, Hristo.

---

### Post by hanexar on 2007-02-08
thanx, but I solve this the hard way : I made a full reinstall :lolflag: Not because of this problem but because I wanted to upgraded to edgy, and I felt like doing a reinstall from a live CD, just because I had never done it before. ;)

---

