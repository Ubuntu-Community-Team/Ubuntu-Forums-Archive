---
title: "Network doesn't connect after switching partitions"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by Mike-97470 on 2007-07-12
I am switching to a new motherboard that only has one IDE channel, so to combine my two IDE drives into one:

1. I copied the ubuntu / drive to an empty partition in another drive using sudo nautilus, set the partition to be / and created a new swap partition.
2. wrote GRUB to the MBR for the new drive/partition.
3. edited menu.lst to correct drive designations so GRUB could find kernel(s). Ubuntu now boots.
4. edited fstab to correct drive designations.
5. fixed sudo (chmod 4755 /usr/bin/sudo)

Now, the net manager doesn't connect (to the internet).  The nm-applet icon is animating, but no connection,

Please give some hints of what to do next!  Thanks.
here's ifconfig---

mike@MikesPavillion:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:20:18:DA:72:3F  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38504 (37.6 KiB)  TX bytes:20574 (20.0 KiB)
          Interrupt:9 Base address:0x8400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

---

