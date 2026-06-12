---
title: "kernel update = lost ethernet"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by BeachBuddah on 2010-12-01
Hi all,

I just updated to the latest Linux kernel today and when I rebooted to complete install my ethernet was gone.  No clue here - I'm posting in Absolute Beginners Talk not because it's a beginner problem but because I need any help you all can give in absolute beginners terminology.  Just let me know what terminal commands to enter and I'll paste all the responses.

Thanks in advance

---

### Post by cariboo on 2010-12-01
Could you paste the ouput of the following command into your next post:

```
sudo lshw -C network > network.txt
```

The above command creates a text file called network.txt that you can copy to the system you are using to post here.

---

### Post by BeachBuddah on 2010-12-01
Cariboo - thanks for the reply - here goes:

```
beachbuddah@beachbuddah:~$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:e00fc000-e00fdfff memory:e00c0000-e00dffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:e00f6000-e00f7fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1.2
       logical name: wlan1
       serial: 30:46:9a:00:73:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ar9170usb driverversion=2.6.35-23-generic-pae firmware=N/A ip=192.168.10.102 link=yes multicast=yes wireless=IEEE 802.11bgn

```

I'm good at the cut n paste thing...let me know what else I need to do :)

---

### Post by BeachBuddah on 2010-12-01
UPDATE:
I rebooted into the previous -22 kernel rather than the -23 I upgraded to today.
I still have no ethernet but instead of being completely non-existent, Network Manager tells me "Device not managed"
Does that help?

---

