---
title: "problem with Wireless configuration"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by sandro54 on 2008-03-05
Hello,
I just started learning Linux (Kubuntu 7.10) but I'm having problems with the Wi-Fi connections, I cannot navigate in Intrnet by Linux but under Windows everything is OK

This is the problem: with wi-fi I can ping my AP (GS624T D-Link) but the ping doesn't work on Internet. 

CAN ANYONE  PLEASE HELP ? THANKS IN ADVANCE......Sandro

following there are the settings of Linux:


Linux_kubuntu 7.10
PC_card_Wlan=Intel(R) PRO/Wireless 3945ABG Network Connection

sandro@linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:5C:72:D0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21

eth1      Link encap:Ethernet  HWaddr 00:18:DE:25:EF:27
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:140 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xe000 Memory:d2100000-d2100fff

eth1:avah Link encap:Ethernet  HWaddr 00:18:DE:25:EF:27
          inet addr:169.254.6.195  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe000 Memory:d2100000-d2100fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12624 (12.3 KB)  TX bytes:12624 (12.3 KB)

sandro@linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"DLINK_WIRELESS"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:140   Missed beacon:0

sandro@linux:~$ sudo iwlist scan
[sudo] password for sandro:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:3E:F4:39:88
                    ESSID:"Alice-21168110"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1804ms ago
          Cell 02 - Address: 00:1B:11:3D:2E:4E
                    ESSID:"DLINK_WIRELESS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-56 dBm  Noise level=-56 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1544ms ago

sandro@linux:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth1
sandro@linux:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp
wireless-essid DLINK_WIRELESS
wireless-channel 11
wireless-mode managed

sandro@linux:~$ cat /etc/resolv.conf

nameserver 193.12.150.2    (DNS of my provider)
nameserver 212.247.152.2   ( DNS of my provider)

sandro@linux:~$   
sandro@linux:~$ ping 169.254.6.195  -c5
PING 169.254.6.195 (169.254.6.195) 56(84) bytes of data.
64 bytes from 169.254.6.195: icmp_seq=1 ttl=64 time=0.030 ms
64 bytes from 169.254.6.195: icmp_seq=2 ttl=64 time=0.033 ms
64 bytes from 169.254.6.195: icmp_seq=3 ttl=64 time=0.034 ms
64 bytes from 169.254.6.195: icmp_seq=4 ttl=64 time=0.034 ms
64 bytes from 169.254.6.195: icmp_seq=5 ttl=64 time=0.034 ms

--- 169.254.6.195 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.030/0.033/0.034/0.001 ms

---

### Post by florizs on 2008-03-05
could you try opening the admin page of your router?
presumably [http://169.254.6.195](http://169.254.6.195)

you could see if http works locally.

---

### Post by ittiam on 2008-03-05
How are you trying to setup the connection? Are you using knetworkmanager or wpa_supplicant from command line or any other thing?

If you are using wpa_supplicant from command line to configure then [ this  ]("http://ubuntuforums.org/showthread.php?t=715391") might help.

---

### Post by unutbu on 2008-03-05
Try 
```

/etc/init.d/networking restart

```

If it doesn't work, post the output here.

You have not yet associated with the AP.
When you ping 169.254.6.195, you are pinging yourself, not the router.

Notice in the output of ifconfig:
```

eth1:avah Link encap:Ethernet HWaddr 00:18:DE:25:EF:27
inet addr:169.254.6.195 Bcast:169.254.255.255 Mask:255.255.0.0

```
This says that your netword adapter, the Intel(R) PRO/Wireless 3945ABG, has ip address
169.254.6.195.

Also notice that in the output to iwconfig it says the Access Point in 'Not-Associated'

```

eth1 unassociated ESSID:"DLINK_WIRELESS"
Mode:Managed Frequency=2.462 GHz Access Point: Not-Associated

```

When you establish a connection with the router, you'll get something like this:

```

Mode:Managed  Frequency:2.457 GHz  Access Point: XX:XX:XX:XX:XX:XX

```

'XX:XX:XX:XX:XX:XX' will be the hardware address of the router.

---

### Post by sandro54 on 2008-03-05
Hi Unutbu,  thanks for your detailed reply

the following the result of the command: etc/init.d/networking restart.

I LOOK FORWARD TO HEARING FROM YOU.    THANKS A LOT  

sandro@linux:~$ sudo /etc/init.d/networking restart
[sudo] password for sandro:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 4401
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:de:25:ef:27
Sending on   LPF/eth1/00:18:de:25:ef:27
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:de:25:ef:27
Sending on   LPF/eth1/00:18:de:25:ef:27
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
sandro@linux:~$

---

### Post by ittiam on 2008-03-05
Well, what I was trying to say is regarding this in your output of iwlist scanning

```

IE: WPA Version 1
Group Cipher : WEP-40
Pairwise Ciphers (1) : WEP-40
Authentication Suites (1) : PSK
```

This is not a right combination, when using WPA the group and pairwise ciphers should be TKIP. I had this problem a day back because of which I was not able to associate myself to the AP and resolved it. This is a bug in gutsy.  That is why I wanted to ask you how are you trying to connect to your AP. Try using knetworkmanager or if you are using wpa_supplicant kindly post your wpa_supplicant.conf.

---

### Post by unutbu on 2008-03-05
Turn off WEP and WPA encryption on your router (temporarily).

The idea is to eliminate as many complications as possible, attain a connection and then build security back into the configuration. 

I can try to help you get as far as a connection with WEP, but unfortunately, I don't have any experience with setting up WPA. The thread

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) 

has a lot of good information, including stuff about setting up WPA. 

So, after you turn off WEP and WPA, and any ESSID hiding or MAC filtering,
try again
```

/etc/init.d/networking restart

```

If that does not work, reboot. You may form a connection immediately, but if not, try the 'restart' command yet again.

Once you get the connection without WEP, 
edit /etc/network/interfaces to include your wireless-essid:

```

auto eth1
iface eth1 inet dhcp
wireless-key <PUT KEY HERE>
wireless-essid DLINK_WIRELESS
wireless-channel 11
wireless-mode managed

```

Enable WEP on your router. Then try to re-establish a connection. This should go smoothly, given that you already succeeded in establishing a WEP-less connection.

Now you would be ready to enable WPA. Good luck!

---

### Post by sandro54 on 2008-03-07
Hi Unutbu
Everything works now. I was able to set up the wireless connection also with WPA protection. The following are the parameters for WPA protection.

1. inside  /etc/network/interfaces
###################### start wireless section.   #######
auto eth1
iface eth1 inet dhcp
wireless-essid "essid_name"
wireless-channel 11
wireless-mode managed
#######################  start  wpa_supplicant          ##############
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
#######################    end wireless section #####

2. inside  /etc/wpa_supplicant.conf

network={
  ssid=&#8221;essid_name"
  psk=&#8221;encryption_key&#8221;
  key_mgmt=WPA-PSK
  proto=WPA
  pairwise=CCMP TKIP
 }


Thanks again for your help.
Sandro54

---

