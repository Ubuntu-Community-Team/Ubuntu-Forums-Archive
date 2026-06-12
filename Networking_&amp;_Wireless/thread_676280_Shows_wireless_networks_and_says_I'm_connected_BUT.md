---
title: "Shows wireless networks and says I'm connected BUT.."
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by hlmijendrix on 2008-01-23
I can't load any pages! wtf?

---

### Post by Hightide on 2008-01-23
Hi, I know its frustrating:confused: but can you give us more information on your wireless setup, type of wireless card, router etc.

we can then give you some suggestions.

regards
:)

---

### Post by hlmijendrix on 2008-01-23
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Does that help at all?

---

### Post by hlmijendrix on 2008-01-23
bump.

---

### Post by hlmijendrix on 2008-01-24
Still need help...

---

### Post by beholdforiambob on 2008-01-24
It is of no help I'm sure but i am having the same problem 

Check it out. I've even got a screen shot. 

[http://ubuntuforums.org/showthread.php?p=4174628#post4174628](http://ubuntuforums.org/showthread.php?p=4174628#post4174628)

what type of card are you using? I'm Using a dlink DWL-520+

---

### Post by hlmijendrix on 2008-01-24
Yup! I have the exact same thing.

My card is a Broadcom something or other...not sure how to check...

---

### Post by chili555 on 2008-01-24
> eth1 IEEE 802.11g ESSID off/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0This suggests you are NOT connected, but the driver is loaded up and the card is waiting for the command to connect to what ESSID. Please do:```
sudo iwlist eth1 scan
```This will tell you the exact name of the router you want to connect to. Remember that Linksys is not linksys is not LINKSYS. Here is a sample scan:```
Cell 01 - Address: 00:0C:41:19:58:77
                    ESSID:"mylittlerouter"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=95/100  Signal level=-49 dBm  Noise level=-87 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001c1e8a7ee1d
```All I would then need to do is:```
sudo iwconfig eth1 essid mylittlerouter
sudo dhclient eth1
```

---

### Post by hlmijendrix on 2008-01-24
Here's what I get...it still doesn't work..same deal :(

```
david@david-laptop:~$ sudo iwlist eth1 scan
[sudo] password for david:
eth1      Scan completed :
          Cell 01 - Address: C6:43:FE:23:28:CB
                    ESSID:"gocats"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:11:5C:04:A3:F0
                    ESSID:"gocats"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:11:5C:04:A3:F2
                    ESSID:"wsc-secure"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : WEP-40 TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : WEP-40 TKIP
                        Authentication Suites (1) : 802.1x

david@david-laptop:~$ sudo iwconfig eth1 essid gocats
david@david-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:7d:20:9e:c7
Sending on   LPF/eth1/00:19:7d:20:9e:c7
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 172.16.0.2
bound to 10.28.210.254 -- renewal in 16508 seconds.

```

---

### Post by chili555 on 2008-01-24
It certainly did work! Look here:> DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 172.16.0.2
bound to 10.28.210.254 -- renewal in 16508 seconds.Try opening Firefox and go to [http://www.google.com](http://www.google.com). Aren't you surfin'?

---

### Post by hlmijendrix on 2008-01-24
No surfing for me! At least wirelessly :( I don't know what the deal is...it's still saying I have a decent signal (50%)...I've always been able to connect up here...

---

### Post by chili555 on 2008-01-24
Let's see:```
ping -c3 172.16.0.2
ping -c3 209.85.165.103 
ping -c3 www.google.com
cat /etc/resolv.conf
```Thanks.

---

### Post by hlmijendrix on 2008-01-24
```
david@david-laptop:~$ ping -c3 172.16.0.2
PING 172.16.0.2 (172.16.0.2) 56(84) bytes of data.
From 169.254.7.207 icmp_seq=1 Destination Host Unreachable
From 169.254.7.207 icmp_seq=2 Destination Host Unreachable
From 169.254.7.207 icmp_seq=3 Destination Host Unreachable

--- 172.16.0.2 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2012ms
, pipe 3
david@david-laptop:~$ ping -c3 209.85.165.103 
PING 209.85.165.103 (209.85.165.103) 56(84) bytes of data.
From 169.254.7.207 icmp_seq=1 Destination Host Unreachable
From 169.254.7.207 icmp_seq=2 Destination Host Unreachable
From 169.254.7.207 icmp_seq=3 Destination Host Unreachable

--- 209.85.165.103 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2025ms
, pipe 3
david@david-laptop:~$ ping -c3 www.google.com
ping: unknown host www.google.com
david@david-laptop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search wsc.edu


nameserver 192.150.175.93
nameserver 192.150.175.59

```

---

### Post by chili555 on 2008-01-24
Now you have me *really* confused! I thought we got an IP address from the DHCP server of ```
bound to 10.28.210.254 -- renewal in 16508 seconds.
```But now your pings are coming from:```
From 169.254.7.207 
```This suggests you are now *disconnected!* What happened between then and now?

May I see:```
ifconfig
```Thanks.

Are you trying to connect wired and wirelessly at the same time? Network Mangler....er, Manager doesn't like that one bit.

---

### Post by hlmijendrix on 2008-01-24
Here's the response I get from the terminal when I'm connected through my wireless..or lack of connection rather ;)

I don't believe I'm trying to connect to both..but here's also a screenshot so you can see what I see..

```
david@david-laptop:~$ david@david-laptop:~$ ifconfig
bash: david@david-laptop:~$: command not found
david@david-laptop:~$ eth0      Link encap:Ethernet  HWaddr 00:16:D4:68:F3:5E  
bash: eth0: command not found
david@david-laptop:~$           inet addr:192.160.97.154  Bcast:192.160.97.255  Mask:255.255.255.0
bash: inet: command not found
david@david-laptop:~$           inet6 addr: fec0::8:216:d4ff:fe68:f35e/64 Scope:Site
bash: inet6: command not found
david@david-laptop:~$           inet6 addr: 2002:c0a0:62ee:8:216:d4ff:fe68:f35e/64 Scope:Global
bash: inet6: command not found
david@david-laptop:~$           inet6 addr: fe80::216:d4ff:fe68:f35e/64 Scope:Link
bash: inet6: command not found
david@david-laptop:~$           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
bash: UP: command not found
david@david-laptop:~$           RX packets:346243 errors:0 dropped:0 overruns:0 frame:0
bash: RX: command not found
david@david-laptop:~$           TX packets:79385 errors:0 dropped:0 overruns:0 carrier:0
bash: TX: command not found
david@david-laptop:~$           collisions:0 txqueuelen:1000 
bash: collisions:0: command not found
david@david-laptop:~$           RX bytes:215989917 (205.9 MB)  TX bytes:9682811 (9.2 MB)
bash: syntax error near unexpected token `('
david@david-laptop:~$           Interrupt:21 
bash: Interrupt:21: command not found
david@david-laptop:~$ 
david@david-laptop:~$ eth1      Link encap:Ethernet  HWaddr 00:19:7D:20:9E:C7  
bash: eth1: command not found
david@david-laptop:~$           inet6 addr: fe80::219:7dff:fe20:9ec7/64 Scope:Link
bash: inet6: command not found
david@david-laptop:~$           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
bash: UP: command not found
david@david-laptop:~$           RX packets:9 errors:0 dropped:0 overruns:0 frame:0
bash: RX: command not found
david@david-laptop:~$           TX packets:424 errors:0 dropped:0 overruns:0 carrier:0
bash: TX: command not found
david@david-laptop:~$           collisions:0 txqueuelen:1000 
bash: collisions:0: command not found
david@david-laptop:~$           RX bytes:2984 (2.9 KB)  TX bytes:36429 (35.5 KB)
bash: syntax error near unexpected token `('
david@david-laptop:~$           Interrupt:22 Memory:d0002000-d0004000 
bash: Interrupt:22: command not found
david@david-laptop:~$ 
david@david-laptop:~$ lo        Link encap:Local Loopback  
bash: lo: command not found
david@david-laptop:~$           inet addr:127.0.0.1  Mask:255.0.0.0
bash: inet: command not found
david@david-laptop:~$           inet6 addr: ::1/128 Scope:Host
bash: inet6: command not found
david@david-laptop:~$           UP LOOPBACK RUNNING  MTU:16436  Metric:1
bash: UP: command not found
david@david-laptop:~$           RX packets:111 errors:0 dropped:0 overruns:0 frame:0
bash: RX: command not found
david@david-laptop:~$           TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
bash: TX: command not found
david@david-laptop:~$           collisions:0 txqueuelen:0 
bash: collisions:0: command not found
david@david-laptop:~$           RX bytes:10193 (9.9 KB)  TX bytes:10193 (9.9 KB)
bash: syntax error near unexpected token `('

```

That's quite the response huh? haha

[img]http://img145.imageshack.us/img145/4743/screenshotoi6.png[/img]

Hopefully this helps! Thanks for everything so far too!

---

### Post by chili555 on 2008-01-24
I don't know what the 'command not found' is all about, but, reading between the lines, you are certainly connected with your wired interface eth0: your IP address is 192.160.97.154.

Please disconnect the wire. Issue these commands:```
sudo ifdown eth0
ifconfig
```Make sure you do *not* see an IP address associated with eth0. Then do:```
sudo dhclient eth1
ping -c3  ping -c3 209.85.165.103 
ping -c3 www.google.com
```Then, if you get ping returns, surf the web.

Network Manager is supposed to seamlessly transition from wired to wireless, but is, in my experience, imperfect.

---

### Post by hlmijendrix on 2008-01-24
```
david@david-laptop:~$ sudo ifdown eth0
[sudo] password for david:
ifdown: interface eth0 not configured
david@david-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:68:F3:5E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:411010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:233221785 (222.4 MB)  TX bytes:11556385 (11.0 MB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:19:7D:20:9E:C7  
          inet6 addr: fe80::219:7dff:fe20:9ec7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4838 (4.7 KB)  TX bytes:54126 (52.8 KB)
          Interrupt:22 Memory:d0002000-d0004000 

eth1:avah Link encap:Ethernet  HWaddr 00:19:7D:20:9E:C7  
          inet addr:169.254.7.207  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Memory:d0002000-d0004000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12094 (11.8 KB)  TX bytes:12094 (11.8 KB)

david@david-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:7d:20:9e:c7
Sending on   LPF/eth1/00:19:7d:20:9e:c7
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
Trying recorded lease 10.28.210.254
PING 10.29.255.254 (10.29.255.254) 56(84) bytes of data.

--- 10.29.255.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
david@david-laptop:~$ ping -c3  ping -c3 209.85.165.103 
ping: unknown host ping
david@david-laptop:~$ ping -c3 www.google.com
ping: unknown host www.google.com

```

Still not loading any pages..

---

### Post by hlmijendrix on 2008-01-24
ok..Don't ask me how I did it..but I actually got it back up and running..I reinstalled and uninstalled and installed some stuff..something did the trick though.I hate computers hah

---

### Post by chili555 on 2008-01-25
Glad it's working!

---

### Post by kung_fu_mike on 2008-06-23
I have all of the exact same issues that --hlmijendrix has had in this thread. The issue does seem to be with the manager. I followed the thread and got it working easily. 

sudo ifconfig eth0 down
sudo dhclient eth1

Those 2 lines are the essential ones. It seems to have something todo with the manager being able to update the lease and cache the old one. Still working with DMSG to try and locate the exact problem and hopefully log the bug.

---

### Post by 01NW14 on 2008-06-24
> **kung_fu_mike said:**
> I have all of the exact same issues that --hlmijendrix has had in this thread. The issue does seem to be with the manager. I followed the thread and got it working easily. 

sudo ifconfig eth0 down
sudo dhclient eth1

Those 2 lines are the essential ones. It seems to have something todo with the manager being able to update the lease and cache the old one. Still working with DMSG to try and locate the exact problem and hopefully log the bug.

I do too have those issues after installing a few updates on gutsy (not migrating to hardy heron) and though the wifi worked at 1st try the 1st time I installed gutsy after windows xp, it didn't work when i formatted. Now, the results of the commands that are on this thread don't always give me the same thing (i mean from when i tried them these previous days, not comparing to hlmijendrix). Is this due to the fact that sometimes-although it says that i'm connected (around 70%) on my network- i can't surf, and sometimes i'm just not connected, or i'm manually configured (which doesn't change a thing, i still can't surf). The command iwconfig shows me my essid but not the bit rate and this:

sudo iwlist eth1 scan
sudo iwconfig eth1 essid mylittlerouter
sudo dhclient eth1

doesn't give me this:

DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 172.16.0.2
bound to 10.28.210.254 -- renewal in 16508 seconds.

my wireless connexion is on wlan0 (i replaced every eth1 by wlan0), and i'm not connected with a wire at the same time (i'm on another computer). My wireless card is a D-Link DWL G630 and i have a WPA key.

Do you think you could help me? This is so frustrating:( Thanx already for your help Chili555, this thread is the one that helped me best up until now :)

---

### Post by 01NW14 on 2008-06-25
I managed to make it work! I think it was some silly problem with my DNS and my key.

:guitar:

---

