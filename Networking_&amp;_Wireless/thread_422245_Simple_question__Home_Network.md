---
title: "Simple question:  Home Network"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by dschmier on 2007-04-25
I have recently installed Feisty on both my desktop and a laptop.  Now, I'd like to share folders from the desktop so that I can access them wirelessly from the laptop.  I've gotten the wireless working on the laptop (I can get an IP address and connect to the internet) and I've followed the instructions at ubuntuguide on setting up nfs server on the desktop.  The folders seems to be "shared" on the server, but I am not able to connect to them from the client.  In fact, I can't even ping the server from the client, so clearly it's just not even seeing the other computer.  Does anyone know what I'm missing (maybe some setting on the router)?  I'm fairly clueless about this networking stuff and this question is so simple that I haven't been able to find anything addressing it on these boards or through google.  Any help would be appreciated.

---

### Post by sdide on 2007-04-25
Do a (as root or with sudo) on both laptop and desktop

~# ip a show

~# ip r show

and post output.

---

### Post by stevieb on 2007-05-05
well, i'll post the results for me: i'm using dapper on both a laptop and a desktop that functions as a file (NFS) and print (CUPS) server.  until recently, i could access the desktop through the laptop with wireless.  after upgrading to feisty, then reinstalling back to dapper, i found i could only connect to the desktop through a wired connection to my router- no NFS, no vncviewer, no CUPS with wireless.

until i did the following: 

ip a show
ip r show

here are the results:


```
steve@darwin:~$ ip a show
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0f:b0:ca:93:82 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:14:a5:9c:78:1d brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.7/24 brd 192.168.1.255 scope global eth1
    inet6 fe80::214:a5ff:fe9c:781d/64 scope link
       valid_lft forever preferred_lft forever
4: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0
steve@darwin:~$ ip r show
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.7
default via 192.168.1.1 dev eth1

```

now, what puzzles me is that after running those two commands, everything works now!

what did those commands do?

thanks,

-steve

---

### Post by stevieb on 2007-05-05
ok, today it doesn't work again; i ran the above two commands, and the only difference is the ip address- yesterday everything worked with 192,168.1.7, and today nothing works with 192.168.1.9.

any ideas why this is?

thanks,

-steve

---

