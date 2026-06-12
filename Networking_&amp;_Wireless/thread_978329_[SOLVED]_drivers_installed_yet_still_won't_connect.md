---
title: "[SOLVED] drivers installed yet still won't connect to internet"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by coolethan on 2008-11-11
i have a Belkin N wireless router and an airlink wireless internet card. i installed the drivers for the card thanks to a thread i was able to find on here with no difficulty. even after doing this i still cannot connect to the internet. the little network icon on the taskbar which used to have and "!" on it is now working and when i select options after right clicking on it it clearly show a wireless network is active thing.

---

### Post by superprash2003 on 2008-11-11
post output of 
1) ifconfig
2) iwconfig
 from the terminal.

---

### Post by coolethan on 2008-11-11
```
ethan@Nertwab:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Ethan's Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:EB:89:F9   
          Bit Rate=54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ethan@Nertwab:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1700 (1.6 KB)  TX bytes:1700 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:e7:2b:86:7c  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:244006 (238.2 KB)  TX bytes:4169 (4.0 KB)
          Interrupt:9 Memory:dffefc00-dffefc25 

ethan@Nertwab:~$ 
```

---

### Post by coolethan on 2008-11-11
on a hunch i went and checked out how my router was set up and everything is connected fine however i searched through the setup a little bit and i found this thing that blocks pinging from other computers and just from the 20 minutes i've spent looking this up i know that you need the two computers to ping each other so i unchecked that box and applied the settings and holy crap it fricken works now.

---

