---
title: "Help With WPA Personal"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by edwin11 on 2007-07-05
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hi all,

i'm using the Linksys WPC54G (ver 1) with Ubuntu Feisty Fawn on my laptop.

i followed the instructions on [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) and managed to get the wireless working WITHOUT wireless security (of course, beforehand i have already done the necessary ndiswrapper stuffs).

(The summary of the instructions in the link above, is to remove all entries in the interfaces file except the "lo" ones, and then to create a /etc/default/wpasupplicant file with the line "ENABLED=0".)

As mentioned, i managed to get the connection established if i turn off wireless security.

However, when i tried to use WPA Personal, it fails to establish the connection.

My router settings:-
Security Mode: WPA Personal
WPA Algorithm: TKIP
WPA Shared Key: somepassphrase
Group Key Renewal 3600 Seconds

Then, in the Network Manager of my laptop:-
(Select "Connect to Other Wireless Network") - because i turned off SSID broadcast
Network Name: mynetwork
Wireless Security: WPA Personal
Password: somepassphrase
Type: TKIP

i just can't work out what is wrong... :confused: any idea?



Thanks in Advance,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by sj3fk3 on 2007-07-05
> **edwin11 said:**
> [FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hi all,
As mentioned, i managed to get the connection established if i turn off wireless security.

However, when i tried to use WPA Personal, it fails to establish the connection.

i just can't work out what is wrong... :confused: any idea?
[/COLOR][/SIZE][/FONT]

You can see whats going on by typing iwevent, thats sometimes does give some insight. Secondly  you can do ps wwaux to see if wpasupplicant is started by the network-manager and if so with what command line. Finally you can always start wpasupplicant by hand and see if you can get a connection that way.

---

