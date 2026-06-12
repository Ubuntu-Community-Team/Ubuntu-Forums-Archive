---
title: "Internet Stopped Working in Feisty"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by j_medic78 on 2007-12-28
I'm at a real loss. My wired and wireless internet had been working fine, then all of a sudden one night I lost connectivity. Network Manager showed that I was still connected to the internet, but I wasn't receiving any information. My wireless network was also showing up, but it would not log in. I tinkered around with stuff, and finally got so frustrated that I reformatted and did a clean install of feisty. Lo and behold there was still no connectivity. I ditched Network Manager, and installed wicd, which still didn't help. I dual boot with Vista, and wireless works fine there. I don't have access to a wired network right now, so I can't check that. I have a Dell E1505, with the intel pro wireless 3495 card, and a broadcom 440x 10/100 controller. Any insight would be much appreciated!

---

### Post by carverj on 2007-12-28
Does Windows use DHCP or static addressing?
In other words, did you have everything configured with the router correctly after re-installing?

---

### Post by j_medic78 on 2007-12-28
Windows is using DHCP. I don't know if this is relevant or not, but using iwconfig, my output is:

lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0 

and output for ifconfig is:

eth0      Link encap:Ethernet  HWaddr 00:19:B9:6A:43:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:01:09:F0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:3 dropped:18 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:590 (590.0 b)  TX bytes:4826 (4.7 KiB) 
          Interrupt:16 Base address:0xa000 Memory:efcff000-efcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:746 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:59756 (58.3 KiB)  TX bytes:59756 (58.3 KiB) 

So anyways, I'm at a complete loss as to why my internet would go down on me, and even after a clean install not work.

---

### Post by j_medic78 on 2007-12-28
Here's iwconfig output again. Maybe this will be a little more useful. This is after trying to connect to my wireless network.

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"HeadHunter Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:C1:36:93:85   
          Bit Rate:24 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/100  Signal level=-77 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:106  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:255   Missed beacon:0

I installed wifi radar as per some of the advice I've seen while perusing through the forums, and it didn't help either. The network manager prompts me for the security code, tries to connect, then prompts me for the code again. Thanks in advance for the help

---

### Post by abedbajia on 2008-03-05
i have the same problem only internet was working at

first and suddenly stopped i think it happened after i installed secuirty

updates on vista

---

### Post by ittiam on 2008-03-05
Now that you are connected to your AP, can you post the output of ifconfig after this.

> **j_medic78 said:**
> Here's iwconfig output again. Maybe this will be a little more useful. This is after trying to connect to my wireless network.

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"HeadHunter Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:C1:36:93:85   
          Bit Rate:24 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/100  Signal level=-77 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:106  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:255   Missed beacon:0

I installed wifi radar as per some of the advice I've seen while perusing through the forums, and it didn't help either. The network manager prompts me for the security code, tries to connect, then prompts me for the code again. Thanks in advance for the help

---

