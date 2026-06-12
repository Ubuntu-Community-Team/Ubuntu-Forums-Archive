---
title: "Cannot connect to wireless router with a cable"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by J4DED on 2007-09-04
I've been searching the forum for an identical issue without luck. I am using Ubuntu (Ubuntu Studio, actually) with Xubuntu and I can see/connect to my wireless router without difficulty when using wireless.

The problem is when I connect to it with a cable that I cannot get network or internet access.

I know that the NIC card works as it works in windows from home connected to the same router with a cable and when I am at work using UbuntuStudio/Xubuntu.

I am on a Thinkpad R51 2887-W1F and the Wirelss Router is a D-Link WBR-1310

Thanks for any help/suggestions.

---

### Post by jimbob on 2007-09-04
I am wondering if your computer has not disconnected the wireless and continues to try to make the connection.  Does the Thinkpad have an antenna switch on the side or something that you can turn off?  Both my HP and Toshiba laptops do. 

In a terminal window enter iwconfig and determine which device is the wireless one; eth0, eth1, wlan0, ath0 etc. and force it to go down, ie ifdown wlan0 (or whatever it is).

See what your ethernet card is by entering ifconfig -a and then try to get it to come up by entering dhclient ethx (whatever x turns out to be)

That's all I can think of for now.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by J4DED on 2007-09-04
My iwconfig output while my wireless connection is active is:> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"lankhmar"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:46:FB:31:38   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:E194-1B04-0E0B-EDBE-044D-2050-6319-CD1E-66AD-268C-DED2-CF78-C08D-731C-AE64-1FF2   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:68  Invalid misc:2   Missed beacon:0

irda0     no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.
My ifconfig -a output is> eth0      Link encap:Ethernet  HWaddr 00:0D:60:79:31:63  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:694878 (678.5 KiB)  TX bytes:26636 (26.0 KiB)
          Base address:0x7000 Memory:d0220000-d0240000 

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:39:CE:2A  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe39:ce2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129651 errors:599 dropped:599 overruns:0 frame:0
          TX packets:73806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:186031504 (177.4 MiB)  TX bytes:6332972 (6.0 MiB)
          Interrupt:11 Base address:0x2000 Memory:d0204000-d0204fff 

eth0:avah Link encap:Ethernet  HWaddr 00:0D:60:79:31:63  
          inet addr:169.254.4.236  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0x7000 Memory:d0220000-d0240000 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5132 (5.0 KiB)  TX bytes:5132 (5.0 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.82.1  Bcast:192.168.82.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.230.1  Bcast:172.16.230.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
The ifdown eth1 command gives the output > ifdown: interface eth1 not configured

The dhclient eth0 command gives me: > Listening on LPF/eth0/00:0d:60:79:31:63
Sending on   LPF/eth0/00:0d:60:79:31:63
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.101 -- renewal in 301346 seconds.

My ethernet connection still does not work. Did I identify the correct ethernet connection? Does my output give any clues?

Thanks...

---

### Post by jimbob on 2007-09-05
It looks to me like your ethernet connection is working fine since your router gave it  an IP as a result of the dhclient request but the wireless appears to be up also so the software is quite content to use eth1 instead of eth0.

Are you using network manager?  Go in and disable the wireless network and reboot and see if it picks up your ethernet connection.

In the meantime maybe someone else will pick up this thread and give us a hand.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

