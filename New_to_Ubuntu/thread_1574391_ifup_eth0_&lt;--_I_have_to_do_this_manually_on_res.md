---
title: "ifup eth0 &lt;-- I have to do this manually on restart"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by cwmoser on 2010-09-14
Everytime I reboot my Ubuntu 10.04, I have to go to the command prompt and execute sudo ifup eth0 in order to get the Network functioning on my home PC.

Not a show stopper but I was wondering where would be a good place to make this happen on startup.  It needs to be run as root and it needs to be at the correct place in the boot up sequence.

How about /etc/rc* but which one makes the best sense?  rc.local? Other places?

Carl

---

### Post by BugBuster on 2010-09-14
Are you using NetworManager?
Please post your /etc/network/interfaces file so that people can help you better.

---

### Post by cwmoser on 2010-09-14
Here is my /etc/network/interfaces file:

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1


On every reboot, I have to manually issue ifup eth0

---

### Post by CharlesA on 2010-09-14
It should look like this:

```
auto eth0
iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1


```

---

### Post by cwmoser on 2010-09-14
That fixed it, thanks.

---

