---
title: "Wifi issue with a Intel 2200bg"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by nexuslogik on 2007-03-22
I am runnign ubuntu 6.10 with a Intel 2200bg pro wireless cord. I am not able to detect this card at all

here is my info

IFconfig:

eth0      Link encap:Ethernet  HWaddr 00:17:08:34:C3:47  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe34:c347/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:830805 (811.3 KiB)  TX bytes:163692 (159.8 KiB)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


route:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


now i have been told by multiple people that this card shoudl work with ubuntu out of the box, but i have reisntalled twice, so i know it is not the veriosn i am installing. I have tried downloading the lastest ipw2200 and matching firmware, i also downloaded the ieee80211. i have attempted to compile, and it works, but i can't seem to get it to b seen even after to pull the firmare into the /lib/firmware directory. i am offically lost

---

### Post by handaxe on 2007-03-22
Folk are right, this card works with ubuntu, so why not for you?

Does this card work under Windoze? Such evidence is NB otherwise one might be chasing one's own tail (does it work off the ubuntu live CD?)

Also does

```
sudo lshw -c network
```  and ```
sudo lspci
``` show the card?

HA

---

### Post by devnulljp on 2007-03-22
That card should work (I have one)
Can you post ourput of 
dmesg | grep ipw2200

Can you try 
sudo modprobe ipw2200

---

### Post by nexuslogik on 2007-03-22
> **handaxe said:**
> Folk are right, this card works with ubuntu, so why not for you?

Does this card work under Windoze? Such evidence is NB otherwise one might be chasing one's own tail (does it work off the ubuntu live CD?)

Also does

```
sudo lshw -c network
```  and ```
sudo lspci
``` show the card?

HA

to answer your question yes it did work with windows, i have not tried the live CD and here is the output from the two commands you said to try

 sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:e8000000-e8000fff irq:11
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
      
so sing lshw -C network, it does see the wifi just fine

lspci responds as seeing it

```
 
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

---

### Post by nexuslogik on 2007-03-22
> **devnulljp said:**
> That card should work (I have one)
Can you post ourput of 
dmesg | grep ipw2200

Can you try 
sudo modprobe ipw2200

i do not see it under the dmesg

---

### Post by chili555 on 2007-03-22
Hmmm. Looks like it's actually an ipw3945. Please install linux-restricted-modules from synaptic and your card should spring to life.
```
eth0 Link encap:Ethernet HWaddr 00:17:08:34:C3:47
inet addr:192.168.1.7 Bcast:192.168.1.255 Mask:255.255.255.0
```Don't forget to disconnect the wire and do sudo ifdown eth0 before you configure your wireless.

---

### Post by nexuslogik on 2007-03-23
> **chili555 said:**
> Hmmm. Looks like it's actually an ipw3945. Please install linux-restricted-modules from synaptic and your card should spring to life.
```
eth0 Link encap:Ethernet HWaddr 00:17:08:34:C3:47
inet addr:192.168.1.7 Bcast:192.168.1.255 Mask:255.255.255.0
```Don't forget to disconnect the wire and do sudo ifdown eth0 before you configure your wireless.

indeed i do have a ipw3945 only problem is. it still doesn;t work.i follow the steps provided on this thread

[http://www.ubuntuforums.org/showthread.php?t=387356&highlight=ipw3945](http://www.ubuntuforums.org/showthread.php?t=387356&highlight=ipw3945)

and still made no progress, nothing has changed at all
i fear i am doing something very wrong in this

---

### Post by nexuslogik on 2007-03-24
ok i finally got the wifi working and i am able to connect to my wifi, however i am nto able to connect when my WPA/WPA2 encryption is enabled. Just as well i am not sure what tool to use to can for open wifi. I know on my mac is used kizmac and on windows i use the default windows tool. i am not all too sure what to use on ubuntu. any ideas

---

### Post by Catsworth on 2007-03-24
HI,

Have a search on the Forums for WICD, that's the GUI I use to manage my wireless connection (supports WPA) and it's been pretty good so far - it's not in the repositories so you'll need to download and install manually, but it's so easy to do that even I managed it :D

---

### Post by Catsworth on 2007-03-24
[LINK]("http://compwiz18.blackhole.cx/wicd/wb/") to WICD home page.

---

