---
title: "Help /etc/resolv.conf keeps changing!"
date: 2005-08-04
forum: Networking &amp; Wireless
---

### Post by anwarlorenzo on 2005-08-04
After some time /etc/resolv.conf keeps changing from my regular DNS servers to 10.0.0.138(which is my gateway ip), and I can't browse! I wonder what's causing this.

I'm connected through pppoe and used pppoeconf to configure things. 

Oh btw sometimes my connection gets dropped and I needed to kill the pppd process and run pppoeconf again to reconnect. Is there a way to reconnect automatically when my connection gets dropped?

Thanks in advance! :)

---

### Post by evilghost on 2005-08-04
Had same issue here.  My fix:

```

sudo apt-get remove resolveconf
sudo rm /etc/resolv.conf
sudo echo nameserver aaa.bbb.cccc.dddd > /etc/resolv.conf

```

Where aaa.bbb.cccc.dddd is the ipaddr of your DNS server.  resolveconf was a big big pain in my butt.

---

### Post by anwarlorenzo on 2005-08-04
Something else is changing it, I don't have resolvconf installed.

```
anwar@hobbes:~$ sudo apt-get remove resolvconf
Reading package lists... Done
Building dependency tree... Done
Package resolvconf is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by evilghost on 2005-08-07
If you look at /etc/resolv.conf I think it's a symlink.  Just nuke the symlink and create resolv.conf from scratch.

Make sense?

---

### Post by anwarlorenzo on 2005-08-07
Actually I fixed that problem by installing:
1. resolvconf
2. pump
3. dnsmasq

I found instructions here: [http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

Now a new problem arises. I don't know what file to edit so that if my line gets dropped, pppoe connects at x times with an interval of y seconds.

---

