---
title: "intel 3945 not showing up as device in ifconfig, etc"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by stairwayoflight on 2007-07-02
Hello,

I just completed a fresh install of feisty and updated all software. I have an HP Pavilion dv2432ca centrino core duo notebook with the intel 3945abg wireless card.

Upon install I noticed that the Restricted Drivers utility shows the driver as active, although when I run ifconfig or iwconfig all I get is entries for eth0 and lo, and "eth1" though I don't know what that is. It wasn't there until I enabled the wireless card by hitting the switch on the front of my laptop. There is an entry for "wireless connection" in the Network dialog now, although it is disabled (box with a dash through it not a checkmark) and I can't enable it with the mouse.

If I run `sudo lshw -short | grep network` this is what I get:
```
$ sudo lshw -short | grep network
/0/100/1c.3/0                    network     PRO/Wireless 3945ABG Network Connection
/0/100/1e/8          eth0        network     PRO/100 VE Network Connection
```

If I run `lsmod | grep 3945` I get:
```
$ lsmod | grep 3945
ipw3945               118816  1 
ieee80211              34760  1 ipw3945
```

So the driver is loaded, I'm just stuck on where to go next. Can anyone help please?

---

### Post by wjp.reg on 2007-07-02
> **stairwayoflight said:**
> Hello,

I just completed a fresh install of feisty and updated all software. I have an HP Pavilion dv2432ca centrino core duo notebook with the intel 3945abg wireless card.

Upon install I noticed that the Restricted Drivers utility shows the driver as active, although when I run ifconfig or iwconfig all I get is entries for eth0 and lo, and "eth1" though I don't know what that is. It wasn't there until I enabled the wireless card by hitting the switch on the front of my laptop. There is an entry for "wireless connection" in the Network dialog now, although it is disabled (box with a dash through it not a checkmark) and I can't enable it with the mouse.

If I run `sudo lshw -short | grep network` this is what I get:
```
$ sudo lshw -short | grep network
/0/100/1c.3/0                    network     PRO/Wireless 3945ABG Network Connection
/0/100/1e/8          eth0        network     PRO/100 VE Network Connection
```

If I run `lsmod | grep 3945` I get:
```
$ lsmod | grep 3945
ipw3945               118816  1 
ieee80211              34760  1 ipw3945
```

So the driver is loaded, I'm just stuck on where to go next. Can anyone help please?

Gees, don't know if I can help but I have the same wireless NIC in my lenovo 3000 N100 and it was operative ater booting into a fresh install of Feisty.  As you mentioned, the restricted driver loaded automatically.  ifconfig and iwconfig do not show a wireless nic, but the 3945abg is set up as eth1 and connected to my wireless router after I configured it's properties using the Network app from the System | Administration menu.  My wireless is secured using 128-bit WEP so once I set the hex passcode and DHCP I was connected.  When I reboot I am asked for my password before the connection is made, but otherwise it is automatic.

As I said, I don't know if that helps.

good luck!

P.S. I get the same output from `sudo lshw -short | grep network` and  `lsmod | grep 3945`

My ifconfig output is 

> eth0      Link encap:Ethernet  HWaddr 00:0F:B0:C8:CD:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:25:58:AB  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe25:58ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48847 errors:0 dropped:1256 overruns:0 frame:0
          TX packets:20579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17577730 (16.7 MiB)  TX bytes:1915513 (1.8 MiB)
          Interrupt:16 Memory:d0000000-d0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5304 (5.1 KiB)  TX bytes:5304 (5.1 KiB)



and iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"HOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:4A:14:8E   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-59 dBm  Noise level=-60 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1257   Missed beacon:0


---

