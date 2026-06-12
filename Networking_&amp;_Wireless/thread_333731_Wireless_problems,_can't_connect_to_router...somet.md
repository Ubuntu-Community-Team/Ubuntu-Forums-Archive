---
title: "Wireless problems, can't connect to router...something obvious I'm not doing?"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by smitjel on 2007-01-07
Running Ubuntu 6.10 on Acer Aspire 3620 with Netgear WGR614v6 wireless router (latest firmware).  I've got the wireless drivers installed via ndiswrapper.  I simply can't connect to my router...what am I doing wrong?

```
root@ubuntu:~# ndiswrapper -l
Installed drivers:
net5211         driver installed, hardware present
``````
root@ubuntu:~# lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@06:05.0
       logical name: wifi0
       version: 01
       serial: 00:16:ce:42:f2:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.2) multicast=yes wireless=IEEE 802.11g
       resources: iomemory:b0100000-b010ffff irq:177
...
``````
root@ubuntu:~# lspci -v | grep Ethernet
06:05.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
``````
root@ubuntu:~# iwconfig
ath0      IEEE 802.11g  ESSID:"Mordor"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx   Security mode:restricted
          Power Management:off
          Link Quality=66/94  Signal level=-29 dBm  Noise level=-95 dBm
          Rx invalid nwid:6650  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
root@ubuntu:~# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:CE:42:F2:4D  
          inet6 addr: fe80::216:ceff:fe42:f24d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
``````
root@ubuntu:~# iwlist scan
Cell 06 - Address: xx:xx:xx:xx:00:6E
                    ESSID:"Mordor"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/94  Signal level=-31 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK
Cell 07 - Address: xx:xx:xx:xx:00:6E
                    ESSID:""
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/94  Signal level=-29 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK
```
It's a little odd to me that the scan on cell 06 and 07 return the same address...could that be part of the problem?  Do I have something setup wrong on the router?  Thanks for any help!

---

### Post by scrooge_74 on 2007-01-07
Are you using encryption or WAP security? Disable the security first and see if you can connect

---

### Post by smitjel on 2007-01-07
```
root@ubuntu:~# iwconfig ath0
ath0      IEEE 802.11g  ESSID:"Mordor"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:00:6E   
          Bit Rate:54 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=65/94  Signal level=-30 dBm  Noise level=-95 dBm
          Rx invalid nwid:317  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Ok, so that worked.  But how do I secure my network?

---

### Post by scrooge_74 on 2007-01-07
Can you tell your router to authenticate the MAC address of your card? Most routers have that capacity, you probably have to log into your route use your browser and type the address of your router and check your security options.

From what I have read this is a better type of security because using encrypted keys can be broken, but using MAC address is better

---

### Post by smitjel on 2007-01-07
So you mean leave security open like I have it, just setup my access list based on MAC address?  And thanks for the help!

---

### Post by scrooge_74 on 2007-01-07
In reality your network is going to be secure, if your router does not know the MAC address of  a wireless card trying to connect it won't let it into the network

If you check in synaptic you are going to find a couple of programs to break encripted keys so for me is a better option for securing my network. 

I use to work in a place where I had setup like this with the MAC address and people had to talk to me before using wireless cards

---

### Post by PilotJLR on 2007-01-07
Just fyi - that is really weak security...

Crackers could still intercept packets and pull information from them; they can also easily spoof a working mac address (obtained from sniffing) and gain full access.

WEP-PSK is also crackable, but it takes more time than breaking mac-only filtering.

WPA is still a secure option.

---

### Post by scrooge_74 on 2007-01-07
But he was having problems right now trying to get things working, now that he knows he can connect he can try other stuff

---

### Post by smitjel on 2007-01-08
Yeah I'll have to play around with the security protocols.  If I can get one of those to work, I'll probably get rid of the mac address filtering strictly for convenience reasons.  I don't want to have to go to my router everytime I want to use a new laptop on my home network...I'd rather just enter a password or whatever.

All I wanted was something to prevent piggy-backing, and mac address filtering will do that just fine for now.  I don't live in an apartment and there's already an abundance of unsecured home networks around me, so I should be good.  I'm also not broadcasting my ssid like these other people are.

Thanks again for the help guys!

---

### Post by scrooge_74 on 2007-01-08
I found this howto which may be usefull for you on securing your lan

[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

---

### Post by PilotJLR on 2007-01-08
> **scrooge_74 said:**
> But he was having problems right now trying to get things working, now that he knows he can connect he can try other stuff

Absolutely! I just mean to say that mac filtering is not a long-term solution, if you need/want security. For a lot of home users, it would be fine.

---

### Post by scrooge_74 on 2007-01-08
Still we manage to put him in the right direction and i learned something new from you today.

---

