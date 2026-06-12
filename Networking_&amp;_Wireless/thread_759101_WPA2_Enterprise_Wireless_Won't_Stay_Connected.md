---
title: "WPA2 Enterprise Wireless Won't Stay Connected"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by jhallward on 2008-04-18
I've been a GNU/Linux user for about a year, and found these forums to be the most useful source for troubleshooting problems during this time, so props to you all.

My problem is that I can connect to non WPA2-Enterprise wireless networks without a problem, but I can't consistently connect to my school's Radius network.  I can only connect on occasion, and when I do connect, I get disconnected after a few seconds, and then can't connect again.  During these few seconds I have a fully functional connection, and can load a few web pages before the connection dies.  The time it takes to die varies, from a few seconds to maybe a minute or two.

Stats:
Kernel: 2.6.24
Card: Broadcom 4311v1
Drivers: b43 (had the same problem with bcm43xx)

There's no relevant dmesg output I could find, or syslog output.  It just tells what I've seen myself from network manager.  I get the same problem with wpa_supplicant btw.  When it fails to connect I NetworkManager just disconnects, while wpa_supplicant gets stuck in a loop of "associated with  <BSSID>" or whatever it says to confirm it's associated.

Here's the tcpdump output from a disconnect event:

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

When I was getting a problem with the same symptoms with bcm43xx and ndiswrapper under kernel 2.6.23 it was because of a bug in my dhcp client daemon.  Issuing dhclient eth1 fixed the problem temporarily, but to fix it permanently I had to downgrade to an older version of dhcpcd (v. 3.2.0).  The same process doesn't seem to work anymore for whatever reason.

---

### Post by jhallward on 2008-04-18
Nevermind, looks like I was doing something wrong with the dhcpcd installation.  For whatever reason I was still running dhcpcd-3.2.3 rather than 3.2.0.  Downgrading fixed my problem, but I can't figure out how to remove my post.  If any mods see this, and feel it's unnecessary, by all means remove it.

---

