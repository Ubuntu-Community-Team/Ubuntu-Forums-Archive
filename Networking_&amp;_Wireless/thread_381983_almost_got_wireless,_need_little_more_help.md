---
title: "almost got wireless, need little more help"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by serendipity576 on 2007-03-11
Hi everyone,
   Well I followed this howto  [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice)) and have gotten through most of it.  Upon the completion of Step 6 and restarting the computer, I then ran iwconfig and got this output.
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Then upon running netstat -rn I get:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1


Then I get to step 8 and run ifdown wlan0, then when I run ifup wlan0 I get this output:

clay@Clay:~$ ifup wlan0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
clay@Clay:~$ sudo ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "XXXXXXXXXXXXXXXXXXXXXXXXXX".
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:16:ce:5e:ea:5c
Sending on   LPF/wlan0/00:16:ce:5e:ea:5c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No working leases in persistent database.......sleeping.


Looks like all the XXXXXs are the problem.  In the howto there was a step that said to enter that but it probably meant for me to enter something else, but I'm not sure what to put there.  Any ideas on this?
   In the networking window it says that the wireless connections is active so....

Thanks

---

### Post by chili555 on 2007-03-11
May we please see cat /etc/network/interfaces, please? Is your router using WEP or WPA? Also, you will probably not readily connect unless you tell your interface what ESSID you want to connect to. People have funny memories, unlike computers. You may remeber setting up your router as linksys. I remember Linksys. My wife swears it's LINKSYS. 

We must have the exact name; close won't do. So let's query the router and ask him, "Hello, what's your name?" sudo iwlist wlan0 scan

When you find the ESSID the router is actually using, do sudo iwconfig essid <what_you_found_not_in_quotes>

Then do sudo dhclient wlan0

Let us know.

PS-If you are not using WEP, you can edit this line out of /etc/network/interfaces before you try the above. ```
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
``` If you are using WEP, put your correct key in its place. It's sure not XXXX

---

### Post by serendipity576 on 2007-03-11
I edited the interfaces and deleted out all the XXXs and now it seems to work.  I DO have another question though, lol.  Everytime I restart my clock reverts to an hour previous.  I tried hitting "Synchronize Now" but it wouldn't change.  Anything on that one.  THanks for your help on that first issue!:) 

Clay

---

### Post by chili555 on 2007-03-11
Are you using a network protocol time server in the USA? Daylight Savings?

---

### Post by Griffiss on 2007-03-11
I am in a similar position to serendipity, just that when I run netstat -rn, there are no numbers under the headings, i.e. no IP addresses etc. 

Any help on how to resolve this would be awesome.

Griff

---

