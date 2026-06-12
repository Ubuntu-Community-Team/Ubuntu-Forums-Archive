---
title: "Connection problems after installing 9.04"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by andy_blah on 2009-04-27
I tried to follow [this]("http://ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html") guide (because I don't have any blank CDs to burn the new Ubuntu), and got to the step in the alternate Ubuntu install (i386) where it would check for DHCP, it didn't manage to get anything, retried a few times, but with the same result. I opted to skip his step and install the connection later. After I have finished installing Ubuntu, I noticed that the connection isn't working. Tried different things to fix this from some guides, but didn't manage to make it work

This is th the result of ifconfig -a :

```
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:76:ae:9a:82  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

pan0      Link encap:Ethernet  HWaddr ee:f0:d4:53:a9:ab  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Note: I don't know from where pan0 appeared, it wasn't there i the previous Ubuntu versions

What should I do to fix this issue?

---

### Post by mikewhatever on 2009-04-27
Check your /etc/network/interfaces. The file should look like this:
> auto lo
iface lo inet loopback

---

### Post by andy_blah on 2009-04-27
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255

auto eth0
iface eth0 inet dhcp
```

This is what /etc/network/interfaces contains

---

### Post by mikewhatever on 2009-04-27
Delete everything below the first to lines. That should get control to the network manager, and you'd be able to set the static parameters from there.

---

### Post by andy_blah on 2009-04-27
Done that, now, can I get any guide to what I should do now? I've never fiddled with the network settings as in the previous Ubuntu installs, the connections worked with no modifications (besides setting PPPoE)

---

### Post by mikewhatever on 2009-04-27
I really hope it will work as in the previous install after a reboot or network restart.
sudo /etc/init.d/networking restart

---

### Post by andy_blah on 2009-04-27
Tried that command and restart too, and it still doesn't work

---

### Post by andy_blah on 2009-04-27
Sorry for bumping, but I am in a hurry...

---

### Post by mikewhatever on 2009-04-27
Do you use DHCP, or is it the setup with the static IP?

---

### Post by andy_blah on 2009-04-27
I don't know exactly what to answer you to that. How could I check out? (n00bish here...)

---

### Post by mikewhatever on 2009-04-27
If you don't know, your setup is most probably DHCP. What's the output of ifconfig now?

---

### Post by andy_blah on 2009-04-27
The same thing as appeared before, just that without pan0 section

---

### Post by mikewhatever on 2009-04-27
How about the output of **sudo lshw -C network**?

---

### Post by andy_blah on 2009-04-28
Here is the output of that command:

```
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:0c:76:ae:9a:82
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

```

---

