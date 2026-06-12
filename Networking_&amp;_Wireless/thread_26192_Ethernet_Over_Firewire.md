---
title: "Ethernet Over Firewire"
date: 2005-04-12
forum: Networking &amp; Wireless
---

### Post by Sputtnik on 2005-04-12
Hi All!

I'm switching my desktop from FreeBSD to Ubuntu (I need a break!), One thing I use a lot
is ethernet over firewire to connect to my laptop (This one stays with FreeBSD 5.3 for now)

On BSD I have device fwe0, and making  "ifconfig fwe0 <ip>" is enought to put firewire
networking up and running (It's a bit faster than normal ethernet!).

How do I use firewire for networking on Ubuntu?

Thanks!

---

### Post by Sputtnik on 2005-04-14
OK, Some googling and I found the following:

Adding modules:

ieee1394
ohci1394
eth1394

reboot

Now ifconfig gives me **eth0**

I connet the laptop (FreeBSD 5.3) to My desktop (Ubuntu 5.04)

On the laptop I type:

ifconfig fwe0 192.168.0.2 ( Has I always did when I had both machines with BSD )

On Ubuntu:

ifconfig eth0 192.168.0.1 up


Doing an ifconfig in both machines shows fwe0 and eth0 configured and active BUT

When I try  a ping , say:

Ubuntu$ ping 192.168.0.2

nothing happens!

BSD$ ping 192.168.0.1

timeout! host down! blah!

What is wrong?

Every thing worked perfectly when I had bsd on both machines!
I just needed to bring up fwe0 with static ip's and voilá.

Any solutions?

Thanks!

---

### Post by coriolan on 2005-06-21
I am doing a similar thing which I reported in [http://www.ubuntuforums.org/showthread.php?t=42770](http://www.ubuntuforums.org/showthread.php?t=42770). I noticed that when eth1394 is in /etc/modules no network connections work. I has to be compiled to the kernel, not just added as a module. After that I get my computers ping eachother.

---

### Post by samat on 2007-08-21
Sorry, can't you write how to compile a kernel with additional module? (I've googled but there is lot's of different ways and I don't know which is better)

---

