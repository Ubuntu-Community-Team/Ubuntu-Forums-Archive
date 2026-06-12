---
title: "SSID recognized, but DHCP failed"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by myodometer on 2007-03-12
I managed to somehow screw up my last install of Ubuntu and decided to reinstall the whole system in order to start from scratch.  I am incredibly new to Linux and don't have the clearest of understandings of how the system works, but I'd like to believe that I'm pretty comfortable around computers.  That being said, I can't seem to get it to connect to the internet.

I'm using a Netgear RangeMax wireless PCI card that has no problem picking up the SSID signal being broadcast from my router.  Only, I can't seem to connect to the internet or ping anything - even on the network.  I manually installed GTKWifi (couldn't install from Synaptic, for obvious reasons) and was receiving a 'DHCP failed' error, despite the fact that GTKWifi would display several local access points that were available.

I am completely lost on this one and would appreciate any and all help in this matter.  As I've seen it asked pretty commonly for problems such as these, I am providing the results of a 'ifconfig -a' Terminal command.  Thanks in advance for your help.

clayton@eightbit:~$ sudo ifconfig -a
Password:
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:FD:F7:FB  
          inet6 addr: fe80::20f:b5ff:fefd:f7fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18333 (17.9 KiB)  TX bytes:2862 (2.7 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:36:C9:EC  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-FD-F7-FB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3260 errors:0 dropped:0 overruns:0 frame:1045
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:309826 (302.5 KiB)  TX bytes:4574 (4.4 KiB)
          Interrupt:201 Memory:e0a60000-e0a70000

---

### Post by chili555 on 2007-03-13
Let's also see these commands: ```
sudo iwconfig
iwlist ath0 scan
iwlist wifi0 scan
```

Thanks. We'll get it!

---

### Post by myodometer on 2007-03-13
Thanks for your reply!  Here are the results of the commands you requested:

[INDENT]clayton@eightbit:~$ sudo iwconfig
Password:
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Safe House"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:13:10:96:F3:D2   
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:406E-7430-6E   Security mode:restricted
          Power Management:off
          Link Quality=26/94  Signal level=-69 dBm  Noise level=-95 dBm
          Rx invalid nwid:211  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
[/INDENT]

[INDENT]clayton@eightbit:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:12:17:62:75:1D
                    ESSID:"linksys-g"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010008ff7f
          Cell 02 - Address: 00:13:10:96:F3:D2
                    ESSID:"Safe House"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
[/INDENT]

[INDENT]clayton@eightbit:~$ iwlist wifi0 scan
wifi0     Interface doesn't support scanning.
[/INDENT]

---

### Post by chili555 on 2007-03-13
Everything looks perfect. Did you try with key open as well as key restricted? No MAC filtering in the router? Also, is the key being broadcast from the router key #1?

---

### Post by myodometer on 2007-03-13
I'm not quite sure what you mean - could you elaborate?

Sorry, I'm a real newb at all this.

---

### Post by chili555 on 2007-03-13
See your iwconfig where it says: ```
Encryption key:406E-7430-6E Security mode:restricted
``` That tells me it will not connect to your router unless the router is set for Shared Key. Here is a post that helps explain this: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

So, sudo gedit /etc/network/interfaces to change it from this: ```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91 restricted
``` to this: ```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91
```
Your interface, ESSID and key will, of course, differ.

Many routers, in their wireless administration page, show 4 WEP keys and broadcast key #3. We need to have key #1 broadcast. Also make sure any MAC filtering in the router is off.

Restart networking: ```
sudo /etc/init.d/networking restart
``` and let us know.

---

### Post by myodometer on 2007-03-13
That seemed to do the trick!

Chili, you're a godsend!  Thanks so much for your help!

---

### Post by dnchari on 2007-03-14
Here is my out put for ifconfig

Computer:$ sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0D:56:58:9F:56  
	  BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
         collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)
            TX bytes:0 (0.0 b)
          Interrupt:169 


eth1      Link encap:Ethernet  HWaddr 00:12:0E:05:78:56  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1
        
  		RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        
 		 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
    
      		collisions:0 txqueuelen:1000 
     
     		RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



lo        Link encap:Local Loopback  
       
   inet addr:127.0.0.1  Mask:255.0.0.0
      
    inet6 addr: ::1/128 Scope:Host
         
 UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
        RX packets:154 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
   
       collisions:0 txqueuelen:0 
  
        RX bytes:11692 (11.4 KiB)  TX bytes:11692 (11.4 KiB)



sit0      Link encap:IPv6-in-IPv4  

          NOARP  MTU:1480  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



and here is the output for iwconfig


Computer:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11g zd1211  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Encryption key:off
          Link Quality=92/100  Signal level=92/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Computer:~$ iwlist lo scan
lo        Interface doesn't support scanning.

Computeri:~$ iwlist eth1 scan
eth1      No scan results


I really apprecaite if you could help setup my USB Wireless adaptor...thanks in advance

---

