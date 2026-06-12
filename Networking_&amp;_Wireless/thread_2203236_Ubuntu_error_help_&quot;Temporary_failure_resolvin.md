---
title: "Ubuntu error help &quot;Temporary failure resolving &quot;us.archive.ubuntu&quot;&quot;"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by Tszar on 2014-02-02
Hey,
What I want to do is set up a local ubuntu file server. I've been going through many forums and other web sites to try to find the solution to this problem. So what happens is that I type ifconfig and I take note of the addresses, inet addr:, Bcast and, Mask.
Then I go and edit the vi /etc/network/interfaces part to match those ip's. I restart the system (/etc/init.d/networking restart). Then type apt-get update and I get this error,
err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
   Temporary failure resolving 'us.archive.ubuntu'

And:

W: Failed to fetch [http://us.archive.ubuntu.dists/precise/Release.gpg](http://us.archive.ubuntu.dists/precise/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu'


Thanks for the help!

---

### Post by chili555 on 2014-02-02
Mind if we have a look?```
cat /etc/network/interfaces
```I suspect you haven't set up DNS nameservers.

---

### Post by Tszar on 2014-02-02
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static 
         address 192.168.1.129
         netmask 255.255.255.0
         network 192.168.1.0
         broadcast 192.168.1.255
         gateway 192.168.1.1
dns-nameservers 192.168.1.1

---

### Post by chili555 on 2014-02-02
I suggest the file be amended to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.129
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1 
```Please be certain that the address you've chosen, 192.168.1.129 in your case, is outside the pool used by the DHCP server in the router so as to avoid collisions.

Get the system to re-read and use the changed file:```
sudo ifdown eth0 && sudo ifup eth0
```And check:```
ping -c3 us.archive.ubuntu.com
```If you get ping returns, you are all set.

---

### Post by Tszar on 2014-02-02
I get a "unknown host us.archive.ubuntu.com"

---

### Post by Iowan on 2014-02-02
Sorry to inject noise into the process...
Please verify that you can ** ping -c3 8.8.8.8**

---

### Post by chili555 on 2014-02-02
> **Tszar said:**
> I get a "unknown host us.archive.ubuntu.com"Can you ping the gateway?```
ping -c3 192.168.1.1
```The DNS server?```
ping -c3 8.8.8.8
```Have you tried a reboot?

Any clues here?```
sudo ifdown eth0 && sudo ifup -vv eth0
```The '-vv' makes the command very verbose and might give us some insight as to what's wrong.

---

### Post by Tszar on 2014-02-02
+3 errors for all
but I just remembered something that I don't know if it is important but when I was setting up the server the installer could not automatically install the DHCP network. so I did it manually. Just another hint to the problem.

---

### Post by chili555 on 2014-02-02
Now we wonder if you have a working ethernet connection at all. Please run and post:```
ifconfig
dmesg | grep eth0
```What was the actual output of the ifup? +3 errors doesn't help us much. Or did it say:```
sudo ifdown eth0 && sudo ifup -vv eth0
```> errorI hope there was more information than that. We need to see it.

---

### Post by Tszar on 2014-02-02
Results for eth0:
IPv6: ADDCONF(NETDEV_UP): eth0: link is not ready
r8169 0000:02:00.0 eth0: link down
IPv6: ADDCONF(NETDEV_UP): eth0: link is not ready
r8169 0000:02:00.0 eth0: link down
IPv6: ADDCONF(NETDEV_UP): eth0: link is not ready
r8169 0000:02:00.0 eth0: link down
IPv6: ADDCONF(NETDEV_UP): eth0: link is not ready
r8169 0000:02:00.0 eth0: link down
IPv6: ADDCONF(NETDEV_UP): eth0: link is not ready
r8169 0000:02:00.0 eth0: link down
IPv6: ADDCONF(NETDEV_UP): eth0: link is not ready
r8169 0000:02:00.0 eth0: link down

The error code:
```
From 192.168.1.129 icmp_seq=1 Destination host unreachable
From 192.168.1.129 icmp_seq=2 Destination host unreachable
From 192.168.1.129 icmp_seq=3 Destination host unreachable 

---8.8.8.8 ping statistics---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2017ms
pipe  3
```

---

### Post by Iowan on 2014-02-02
Not a good sign...
What are results of 
```
ifconfig -a
sudo lshw -C network
```
Check cable connections.

edit: Just noticed that those are IPv6 messages...

---

### Post by Tszar on 2014-02-02
I fixed my issue thanks for your help

---

### Post by Iowan on 2014-02-02
We're anxious to hear what fixed it!
Afterward you can mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

