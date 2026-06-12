---
title: "static ip help! /etc/network/interfaces"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Deadmode on 2008-05-02
I'm using gOS which is built off of ubuntu 7.10.  I've been trying to setup my box to have a static ip. My /etc/network/interfaces file looks like this.
```
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

The ip, netmask, network info is generic.  When I reboot my computer I can't ssh or vnc into it.  But, I can get it to work when I do this
```
sudo /etc/init.d/networking restart

```
I get
```
 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
SIOCDELRT: No such process
                                                                         [ OK ]

```
And then everything works fine.  But, on reboot it all goes back to crap mode.

---

### Post by p_quarles on 2008-05-02
I've moved this to Networking & Wireless. I don't think it's a beginner's question, and more importantly, I think it may have a better chance of getting answered here.

---

### Post by Deadmode on 2008-05-02
> **p_quarles said:**
> I've moved this to Networking & Wireless. I don't think it's a beginner's question, and more importantly, I think it may have a better chance of getting answered here.

Sorry for misplacing it. Thank you for moving it.

---

### Post by SpaceTeddy on 2008-05-02
when your network is not configured after boot - what does ifconfig say ? what output does it produce ? in other words, it the interface brought up properply during boot time, or is it only brought up upon a network restart ?

---

### Post by Deadmode on 2008-05-03
on boot up my ip is changed to something different than what I'm specifying in /etc/network/interfaces.  The ifconfig looks like this ```
eth0      Link encap:Ethernet  HWaddr 00:0D:87:39:A1:CE  
          inet addr:192.168.0.***  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe39:a1ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9476422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10166314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1177573634 (1.0 GB)  TX bytes:1565770444 (1.4 GB)
          Interrupt:11 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:115070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13663456 (13.0 MB)  TX bytes:13663456 (13.0 MB)


```
I get this after /etc/init.d/networking restart ```
* Reconfiguring network interfaces...
RTNETLINK answers: No such process
SIOCDELRT: No such process
```
But after the restart, the static ip address that I specify in /etc/network/interfaces is then applied and everything works as planned. But, on restart everything is messed up again and a different ip address is set.

---

### Post by SpaceTeddy on 2008-05-04
mhm - maybe this helps - i commented some lines out in your interfaces. example is below
```
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#        script grep
#        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

i have never seen that hotplug stuff before... what happens if you remove it, does that then bring up your network config correct ? also - why has you network card a transfer of 1.4/1.0 Gbyte after boot ? that makes no sense. are you loading some stats from somewhere ?

i know, question over question :) hope they help

---

### Post by Deadmode on 2008-05-05
Thank you for your suggestion, but it doesn't seem to do anything.  I only added those lines in because I was copying a tutorial I saw online.  I used to have this in the /etc/network/interfaces file. ```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
auto eth0
```
This wasn't working for me.  Oh ya that ifconfig output wasn't directly after boot up.  But, it had been rebooted and was sitting there for a while before I started looking for the output of ifconfig. Thanks. ](*,)

---

### Post by Paris Heng on 2008-05-05
> **Deadmode said:**
> Thank you for your suggestion, but it doesn't seem to do anything.  I only added those lines in because I was copying a tutorial I saw online.  I used to have this in the /etc/network/interfaces file. ```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
auto eth0
```
This wasn't working for me.  Oh ya that ifconfig output wasn't directly after boot up.  But, it had been rebooted and was sitting there for a while before I started looking for the output of ifconfig. Thanks. ](*,)

Restart your network every time after setting.

> /etc/init.d/networking restart

---

### Post by Deadmode on 2008-05-05
Ya I have to do that everytime after bootup or if the computer sits too long.  I don't want to do that anymore.  I want it to use the static ip that I'm attempting to assign to it.

---

### Post by Deadmode on 2008-05-07
still nothing yet I've been combing the internet about what could be the problem.  I did notice that the ip that my box keeps changing to is the starting ip address on my router. Although when I change it on my router it doesn't seem to make a difference at all. IDK my bff Jill! ](*,)

---

### Post by Deadmode on 2008-05-14
i hate to do this, but I don't want to make a new post.  Does anyone have any idea for me? bump

---

### Post by Iowan on 2008-05-14
Try   **ps aux |grep dhclient**    I'm wondering if dhclient may be updating your "static IP" with one of it's choosing.

---

### Post by Deadmode on 2008-05-19
I attempted to change dhclient to non executable, but the ip still changes.  So, I think I'm just going to start from scratch and try out xubuntu.  Thanks for your help.

---

