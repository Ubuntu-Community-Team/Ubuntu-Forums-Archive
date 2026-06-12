---
title: "Intel 4965 AGN works at home but not work"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by bosp7 on 2007-10-22
I'm using 7.10 on a new laptop with a Intel 4965 agn card.  The card works fine at home, but when I try to connect to my work wireless it won't connect. 

At work WPA Enterprise with PEAP is being used, and I have been able to get a different laptop with 7.10 and a different wireless card working fine.

Any ideas?

---

### Post by bosp7 on 2007-10-22
this is what is output after running sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                                       There is already a pid file /var/run/dhclient.wlan0.pid with pid 10363
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:d7:51:cd
Sending on   LPF/wlan0/00:13:e8:d7:51:cd
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:d7:51:cd
Sending on   LPF/wlan0/00:13:e8:d7:51:cd
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by bosp7 on 2007-10-26
I've actually just gotten it working using ndiswrapper, but it's not perfect.  I've tried running a speed test twice, and it causes the computer to lockup, and I have to reboot.

Does anyone have any ideas why it might work using ndiswrapper but not the native iwl4965 drivers?  I would really like to be able to get this working using the native linux drivers

---

### Post by GICodeWarrior on 2008-01-17
> **bosp7 said:**
> At work WPA Enterprise with PEAP is being used, and I have been able to get a different laptop with 7.10 and a different wireless card working fine.


I have a ThinkPad x61s with the Intel PRO/Wireless 4965 AGN chipset, and I am having similar trouble.

Connecting to unsecured wireless networks gives me no trouble.  Connecting to a wpa-enterprise network is a PITA.  It works on occasion, but I have not found anything repeatable I can do to get it to work.

I have tried both Gutsy and Hardy with the same problem.  I also have this problem with an Atheros card I have.

My network supports both WPA enterprise and WPA2 enterprise, with AES or TKIP, and PEAP-GTC or TTLS-PAP.  I always specify the CA certificate.

I have access to the AP's and the freeRADIUS server if log snippets from either would help...

Any suggestions are appreciated.

---

### Post by jhallward on 2008-04-18
Same problem.  When I do connect "on occasion" (as mentioned above) I get disconnected again after a few seconds (long enough to load a web page or two).  Here's the tcpdump output when I get disconnected:

11:51:40.870387 00:d0:02:29:34:00 (oui Unknown) Unknown SSAP 0x8c > 00:1c:b3:c5:e8:ad (oui Unknown) Unknown DSAP 0x5c Information, send seq 0, rcv seq 16, Flags [Command], length 1500
11:51:40.870872 00:d0:02:29:34:00 (oui Unknown) Unknown SSAP 0x8c > 00:1c:b3:c5:e8:ad (oui Unknown) Unknown DSAP 0x5e Information, send seq 0, rcv seq 16, Flags [Command], length 1500
11:51:41.698297 IP <my school's IP>.56022 > 205.188.9.125.aol: P 3625:3631(6) ack 30068 win 62560
11:51:42.888418 IP <my school's IP>.56022 > 205.188.9.125.aol: P 3625:3631(6) ack 30068 win 62560
11:51:43.674814 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x28 Information, send seq 0, rcv seq 16, Flags [Command], length 92
11:51:43.737170 
11:51:43.741025 EAP code=1 id=0 length=58 
11:51:43.741090 EAP code=1 id=0 length=11 
11:51:43.748290 EAP code=1 id=0 length=6 
11:51:43.748469 EAP code=1 id=0 length=113 
11:51:43.761036 EAP code=1 id=0 length=1020 
11:51:43.761156 EAP code=1 id=0 length=6 
11:51:43.767282 EAP code=1 id=0 length=894 
11:51:43.790542 EAP code=1 id=0 length=204 
11:51:44.696962 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x28 Information, send seq 0, rcv seq 16, Flags [Command], length 193
11:51:45.035212 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2a Information, send seq 0, rcv seq 16, Flags [Command], length 208
11:51:46.568204 IP <my school's IP>.56022 > 205.188.9.125.aol: P 3625:3631(6) ack 30068 win 62560
11:51:47.359190 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2a Information, send seq 0, rcv seq 16, Flags [Command], length 383
11:51:47.973396 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2c Information, send seq 0, rcv seq 16, Flags [Command], length 383
11:51:47.973604 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2c Information, send seq 0, rcv seq 16, Flags [Command], length 146
11:51:48.382870 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2e Information, send seq 0, rcv seq 16, Flags [Command], length 133
11:51:48.386030 00:d0:02:29:34:00 (oui Unknown) Null > 00:13:02:7b:32:73 (oui Unknown) Unknown DSAP 0x2e Information, send seq 0, rcv seq 16, Flags [Command], length 166
tcpdump: pcap_loop: recvfrom: Network is down
2063 packets captured
3244 packets received by filter
1181 packets dropped by kernel

now if only I knew what SAP was (I'm guessing DSAP is destination SAP and SSAP is source SAP).

---

