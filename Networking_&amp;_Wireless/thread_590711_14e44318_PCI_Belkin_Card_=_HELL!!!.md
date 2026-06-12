---
title: "14e4:4318 PCI Belkin Card = HELL!!!"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by AtomBombCalamari on 2007-10-25
ok Im noob....


I've got the Belkin Wireless PCI adapter problem, ive tried several tuts, tried the bcm43xx firmware that comes with Gutsy, although i had to download a bcm43xx-fwutter file anyways. Im not connected to the internet wired, so i have to switch back and forth from ub and win. The following are my system specs and some outputs for commands. 

What Im running:
Custom Built pc w/ pentium4 ht

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:11:5B:63:85:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:11:50:62:3B:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Memory:fa000000-fa002000 

eth1:avah Link encap:Ethernet  HWaddr 00:11:50:62:3B:44  
          inet addr:169.254.4.24  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Memory:fa000000-fa002000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:173629 (169.5 KB)  TX bytes:173629 (169.5 KB)

ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318 ) present (alternate driver: bcm43xx)

So it looks like it should be working to me. The System>Admin>Network gui has the wireless checked, no other connection checked, and the properties for the wireless are not roaming(i have my network and password punched in.) if i try to do roaming no networks can be seen.(there are at least 5 at all times in windows) The gui in the DNS tab shows two dns severs that look like the right ones, and i didnt enter those, it retrieved them itself. When I try to open a browser it doesnt give the page couldnt be loaded. It just says looking for [www.google.com](www.google.com) or whatever address i enter. 

I read this dig article that was the top 15 reasons to switch to Linux this year....
 my favorite reason was the Army of super nerds waiting to help everyone who doesn't know linux....well let's see your army.:) and no offense should be taken by the term super nerds, im total nerd, just not super yet...i have a few more programming lenaguages to learn, including linux commands.

---

