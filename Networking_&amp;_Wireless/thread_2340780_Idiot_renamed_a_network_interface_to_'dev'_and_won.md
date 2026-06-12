---
title: "Idiot renamed a network interface to 'dev' and won't connect to wifi now."
date: 2016-10-22
forum: Networking &amp; Wireless
---

### Post by andybfmv96 on 2016-10-22
Hello,

Thanks for viewing my post, this is my first post up here and actually one of my first times using linux so im a total dumb@** with this.

Anyways, to the nitty gritty:

While messing around with a few vm's, I accidentally ran this command in my host's terminal:

```
sudo ip link set name dev wlp5s0
```

It looks like it renamed my internal wifi card to "dev"
Additionally, i can see wifi networks, but cannot connect to them. (afraid to reboot)

originally, running an 'ip addr' would output this: 

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 44:8a:5b:6d:c4:c4 brd ff:ff:ff:ff:ff:ff
3: wlp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 10:08:b1:8a:ca:6f brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.181/24 brd 192.168.1.255 scope global dynamic wlp5s0
       valid_lft 82409sec preferred_lft 82409sec
    inet6 fe80::157d:700b:f311:91df/64 scope link 
       valid_lft forever preferred_lft forever

```

Now this is the output: 

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 44:8a:5b:6d:c4:c4 brd ff:ff:ff:ff:ff:ff
3: dev: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 10:08:b1:8a:ca:6f brd ff:ff:ff:ff:ff:ff
5: wlx98ded00b0dc3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 98:de:d0:0b:0d:c3 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.151/24 brd 192.168.1.255 scope global dynamic wlx98ded00b0dc3
       valid_lft 85481sec preferred_lft 85481sec
    inet6 fe80::a518:6353:6a1a:ca23/64 scope link 
       valid_lft forever preferred_lft forever

```


I am not sure how to fix this, i am trying to avoid reinstalling my distro every single time i have a problem. I would much rather learn from experience and fixing problems on my own. Thank you in advance for any help provided. It is very appreciated.

p.s. i know im totally dumb for doing that. I'm sure its a first running a command in the wrong machine.

---

### Post by andybfmv96 on 2016-10-22
Okay, a reboot fixed this, this thread can be deleted.

However if anyone has the time, id love to know what this command actually did so i can learn from it.

---

### Post by kpatz on 2016-10-22
As far as I can tell, you simply changed the name of the interface from "wlp5s0" to "dev".  The man pages for the ip command aren't very helpful.

You could undo the change by simply reversing the command:

```
sudo ip link set name wlp5s0 dev
```

But since you said rebooting fixed it, you should be good to go.  Did the interface name change back to wlp5s0 or is it working as "dev" now?

---

