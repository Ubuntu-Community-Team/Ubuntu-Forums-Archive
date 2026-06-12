---
title: "Realtek problem w/ screen shots"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by SikEnCide on 2007-04-19
ok soo i went to realteks website and got the lan drivers because my lan connection wont show up.  it is a realtek RTL8111/RTL8168B 10/100/1000 nic  its on a laptop if that matters.

wireless works fine.. but now lan

interesting thing tho.. look at the screen shots 





[IMG]http://img.photobucket.com/albums/v222/jugganinja/ubuntu/Screenshot-Devices-NetworkTools.png[/IMG]
[IMG]http://img.photobucket.com/albums/v222/jugganinja/ubuntu/Screenshot-Devices-NetworkTools-1.png[/IMG]
[IMG]http://img.photobucket.com/albums/v222/jugganinja/ubuntu/Screenshot-Devices-NetworkTools-2.png[/IMG]


i am so confused can anyone help me.. id rather use my lan instead of wireless.. but at least i have something for now

---

### Post by mr charel on 2007-04-19
i have the same problem :s

when I do:
```
lshw -C network
```
I get:
```

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: **:**:**:**:**:**
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 multicast=yes
       resources: ioport:c800-c8ff iomemory:fe0ff000-fe0fffff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: **:**:**:**:**:**
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fe1ff000-fe1fffff irq:17

```

sry for making you excited about nothing

SikEnCide could you do
```
lshw -C network
```
and see what you get?

---

### Post by SikEnCide on 2007-04-19
i got all excited to see an answer to the post.. only to see you have the same problem.

:mad: ](*,)

---

### Post by SikEnCide on 2007-04-19
ok i did it

```
chris@Sik:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:0e:f6:88
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:c800-c8ff iomemory:fe0ff000-fe0fffff irq:16
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:fe1ff000-fe1fffff irq:17

```


strange thing.. i rebooted a few times while doing things.... **it works now**

---

### Post by mr charel on 2007-04-20
yeah now it works but i hope i don't have to boot several times to keep it working

---

### Post by SikEnCide on 2007-04-22
yeah well its not working for me now

---

### Post by gborzi on 2007-04-22
Hello, I'm having a similar problem with the same RTL8111/8168B NIC. After some time spent on "trial and error" I have found that the kernel driver (r8169) does not work correctly if it's loaded while the cable is unconnected, but works correctly, being also able to detect link beats, otherwise. In other words:
1) Load r8169 while unconnected -> no link beat and NIC not working.
2) Load r8169 while connected -> link beat works, you can connect/disconnect your cable with the driver working.
So, a way to get the ethernet working if it's not working, is to connect the cable and > sudo modprobe -r r8169
sudo modprobe r8169
Hope this helps.

---

### Post by SikEnCide on 2007-04-23
hmm interesting.. its funny as my wireless works fine...  i will surely try this later today when im done with class.

---

### Post by gborzi on 2007-04-23
Look here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798) .

---

### Post by SikEnCide on 2007-05-10
this doesnt seem to work either.... its driving me crazy sometimes it works sometimes it doesn't its not consistent at all, i think realtek needs to fix their damn drivers

---

### Post by SikEnCide on 2007-08-03
soo is there any other idea's im lost in the dark im not too productive using ubuntu, but im tired of windows

---

