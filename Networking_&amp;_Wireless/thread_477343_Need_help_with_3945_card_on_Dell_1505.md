---
title: "Need help with 3945 card on Dell 1505"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by sdbrown219 on 2007-06-18
Hey I need help. I am new to Ubuntu and so far everything has gone smooth with the exception of my wireless card. have tried using restricted drivers as well as using ndiswrapper. none of this worked. My wifi light just flashes. Trying to use Wifi Radar as a network manager. It does pick up networks but will not connect. Any help would be appreciated. (Using Ubuntu 7.04)

---

### Post by charleseddy on 2007-06-18
Try to connect to one.  Then open an empty terminal and type ifconfig, then iwconfig.  Paste the results into this thread.

ce

---

### Post by sdbrown219 on 2007-06-18
I don't have an option to connect. Wifi Radar only has a disconnect option and says that I am connected to none.

---

### Post by kevdog on 2007-06-18
I helped this guy with a Dell with his problem:
[http://ubuntuforums.org/showthread.php?t=476662](http://ubuntuforums.org/showthread.php?t=476662)

Possibly this link will help you.  I you are planning on using ndiswrapper, you will need to compile from source.  Ive found the version in the repositories do not help.  Read the link I posted, it will help you uninstall ndiswrapper (completely -- very important). And then help you reinstall it from source.

What is different about your problem versus the one in the post above is your wireless card -- you will need a different driver.  When we get to that point -- we can solve that problem, so no worries.

---

### Post by tnmarktx on 2007-06-19
I think he already tried to compile ndiswrapper from the source.  I tried helping him with it using this how to:

[URL="http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501"]

I have the 1501 and it worked great for me.  I figured that it would work on his by just changing the driver from Dell and blacklisting the driver that his computer was trying to use.  Everything that he had read led him to believe that his card would work from the get go.  However, when activating has wifi, the light would just blink instead of staying on solid.  We achieved the same result after using the procedure with ndiswrapper.  I hope this helps.

---

### Post by sdbrown219 on 2007-06-19
ifconfig gives this:


eth0      Link encap:Ethernet  HWaddr 00:19:B9:51:CC:3C  
          inet addr:68.52.139.194  Bcast:255.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::219:b9ff:fe51:cc3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:593350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44923306 (42.8 MiB)  TX bytes:758707 (740.9 KiB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1869 (1.8 KiB)  TX bytes:1869 (1.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:19:D2:01:9E:C6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:77 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xe000 Memory:efcff000-efcfffff 

wlan0:ava Link encap:Ethernet  HWaddr 00:19:D2:01:9E:C6  
          inet addr:169.254.8.23  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xe000 Memory:efcff000-efcfffff 



iwconfig gives:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:80   Missed beacon:0

---

