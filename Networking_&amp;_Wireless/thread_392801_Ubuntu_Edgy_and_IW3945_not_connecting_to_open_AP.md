---
title: "Ubuntu Edgy and IW3945 not connecting to open AP"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Ender Black on 2007-03-24
Hmmm... I am sure this is a super easy problem but I cannot seem to figure it out.  I have Ubuntu Edgy loaded on HP Pavillion dv9000.  I have a Intel PRO/Wireless 3945abg network card, but I cannot seem to get it to connect to the OPEN AP at the hotel I am at.  Wired connection is fine.  Here are the results of all the trouble-shooting efforts I have tried following advice on the forums:

**iwconfig**
eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:845   Missed beacon:0

**lshw**
*-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth1
                version: 02
                serial: 00:18:de:6f:16:8f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 multicast=yes wireless=unassociated
                resources: iomemory:d8000000-d8000fff irq:169


**lspci**
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

From what I can tell, Ubuntu sees the device and the driver is loaded.  I could connect to a secure AP through network manager, but it isn't allowing me to enable the card to connect to a open AP.

Any thoughts... I am sure I am going to slap myself in the forehead and groan when I see the answer to this.

Thanks in advance.

---

### Post by Ender Black on 2007-03-25
ehh... apparently I took my stupid pill instead of my vitamins this morning... case solved....

thanks

---

### Post by bdidihey on 2007-03-25
Ok I must be having stupid pills as well-
Trying the new Feisty- Everything seems fine- BUT.............

I have a very similiar problem- it appears I am associated with my AP - on eth1- but i never get an IP address- wired is fine -
I shut off all encryption on the AP- 
I tried a static address-no success-
Windows on the same PC associates fine-

Wireless Card INTEL 3945abg/ Sony Laptop n160

IDEAS?? I would be most GRATEFUL!! 



**ifconfig**

eth0      
Link encap:Ethernet  HWaddr 00:13:A9:4D:54:90  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe4d:5490/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:551961 (539.0 KiB)  TX bytes:123004 (120.1 KiB)
          Interrupt:17 




eth1      Link encap:Ethernet  HWaddr 00:18:DE:BE:CB:DB  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121 errors:10 dropped:18 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27905 (27.2 KiB)  TX bytes:4183 (4.0 KiB)
          Interrupt:18 Base address:0x2000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11095 (10.8 KiB)  TX bytes:11095 (10.8 KiB)
[B]
 iwconfig[/B]
lo        no wireless extensions.



eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"test"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:18:F8:4E:AE:59   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-26 dBm  Noise level=-27 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

---

### Post by chili555 on 2007-03-25
There are several other posts floating around on this subject and it seems to have to do with your computer not wanting to take two separate IP addresses from two interfaces at the same time. Network Manager specifically forbids it (but it can be tricked). Some people do it and have no trouble, others, including me, have no end of network problems when they try it. 

When you are connected via ethernet, it is very hard to diagnose and fix wireless problems because you may not be associated with the access point, yet you can ping and pull web pages.

You might try disconnecting the wire, do sudo ifdown eth0, and then try getting an IP wirelessly.

---

### Post by bdidihey on 2007-03-25
Is the "ifdown eth0" any different than disabling it in the Network GUI??

---

### Post by chili555 on 2007-03-25
No, it's just the way old grey-bearded linux geeks do it. No difference, AFAIK.

---

### Post by bdidihey on 2007-03-25
That makes me feel better anyway-

Any other suggestions?? I was starting to think I had lost my mind

I have have done quite a bit of searching- but nothing seems to be quite like this could you point me to those threads???

Thanks
B.

---

### Post by bdidihey on 2007-03-26
Just for fun 

I did disable eth0 and eth1 (in terminal)  - then enabled eth1 

BOOM an IP address appears- so thanks for the help

---

