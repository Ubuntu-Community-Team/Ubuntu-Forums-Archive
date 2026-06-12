---
title: "WLAN (sometimes) not connecting"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by laffinet on 2007-12-21
This is driving me nuts and if I can't resolve this I might have to go back to XP (which would be a shame).

I had my wireless network configured (manually, I followed some suggestions and removed Network Manager after I had a lot of problems) and everything was working fine. 

I did not change a thing, but when I booted today I could not connect to my router anymore. Here's my interfaces:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid wireless
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 6b0c9b82802cbc1fbdfa5ee439b333ca19dc3a7044db288e57bc915e1ff9571c
```

This is what I get from iwlist scan:
```
 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:60:64:09:2F:6E
                    ESSID:"wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:100  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 272ms ago
```
And this is what sudo /etc/init.d/networking restart produces (eth0 is my wired conenction):
 ```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 4795
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0c:f1:19:47:29
Sending on   LPF/eth1/00:0c:f1:19:47:29
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5749
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:03:9d:75:12:11
Sending on   LPF/eth0/00:03:9d:75:12:11
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0c:f1:19:47:29
Sending on   LPF/eth1/00:0c:f1:19:47:29
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:03:9d:75:12:11
Sending on   LPF/eth0/00:03:9d:75:12:11
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 1371 seconds.
                                                                         [ OK] 
```

I've searched this forum for hours and tried lots and lots of things, nothing worked.

Seriously, this is driving me nuts. What is wrong, what can I do ? Can someone help me please !!!!

I don't want to go back to XP, but not having a working wireless connection is very annoying.

Thanks.

---

### Post by laffinet on 2007-12-21
I forgot, here's my iwconfig:

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"wireless"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by ubutufan on 2007-12-21
Go to the interfaces file (/etc/network/interfaces) and make a backup.
Then edit the file and make sure you have the following only

----------------
auto lo
iface lo inet loopback
----------------

Nothing else.
Save the file and reboot ubuntu

Is it working? Are you using Wicd or what?

Let us know

---

### Post by laffinet on 2007-12-21
> **ubutufan said:**
> Go to the interfaces file (/etc/network/interfaces) and make a backup.
Then edit the file and make sure you have the following only

----------------
auto lo
iface lo inet loopback
----------------

Nothing else.
Save the file and reboot ubuntu

Is it working? Are you using Wicd or what?


No, this did not work. And I'm not sure how this could have worked, doesn't this pretty much eliminate any wireless configuration ?

> **ubutufan said:**
> 

Is it working? Are you using Wicd or what?

Let us know

I did try Wicd, but that didn't work either. Got stuck at the "obtaining IP" bit.

Just to clarify:
1. wired network to my router is working fine
2. I did have wireless working just fine (with the setup described earlier), I did not change anything and now it's not working.

---

### Post by ubutufan on 2007-12-21
Hi Laffinet
I suggest you go back to wicd.
Make sure that you follow the steps for the network file.
The fact that you are not obtaining an ip is not a matter of ubuntu. it is a matter of the router. Two things to investigate. First if the router is allowing mac addresses of your machine. Is there a possibility that you have restricted the mac access in your router?
Second. Go with static addresses. Make sure your router is properly configured to accept static ips and then assign necessary ip to your machine. Next make sure the subnet is correct.
last but not least the gateway(router ip) make it same as primary DNS. you may use secondary DNS the one of your ISP
Give as much info as possible if this does not work

---

### Post by ubutufan on 2007-12-21
[QUOTE=laffinet;3990893]No, this did not work. And I'm not sure how this could have worked, doesn't this pretty much eliminate any wireless configuration ?


You are partially correct. it eliminates any previous connect attempts. Example is that if you connect to another wireless, all data connection is recorded in the networks file. This file stores just about everything. Sometimes causing malfunction of connections. It would (on occasions loop to the first configuration encountered)
I am sure ubuntu developers have noticed it and will eventually take measures

---

