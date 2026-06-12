---
title: "Gigabyte GN-WP01GS WiFi Card Not Working"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by elmer_42 on 2008-05-08
Today I realized that I had connected to the wrong WiFi network. I know that I have used my personal WiFi network before, but I accidentally connected to the wrong one earlier. I switched back to my WiFi network, and the WiFi stopped working. The network I was connected to before didn't work and my personal WiFi network didn't work. There are other computers connected to the network, and they access the internet just fine. I can connect to 192.168.1.1, the configuration page for my router, but the internet is not working.

The only difference I have noted is this: Before this problem, the WiFi driver I use was in Restricted Driver Manager (or whatever it is called, I am on my Windows partition right now), but now it is not. I don't know if this is a result or cause of the problem or if it is because of my upgrade to Hardy. I've got to switch back to Ubuntu to run ifconfig and iwconfig and save them to a new file, because apparently Notepad++ doesn't like the one I saved before. Just know that i(w|f)config is on its way. :)

Thank you for your time. Please help if you can.

**e:** Here is the output of iwconfig and ifconfig.
```
staylor@Mariner:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

staylor@Mariner:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:93:c5:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101404 (99.0 KB)  TX bytes:101404 (99.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7d:34:8f:3e  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-7D-34-8F-3E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by elmer_42 on 2008-05-08
So... nobody knows?

---

### Post by elmer_42 on 2008-05-08
Well this stinks. Guess I'm going to have to format, reinstall, and reconfigure. See you on the flip side!

---

