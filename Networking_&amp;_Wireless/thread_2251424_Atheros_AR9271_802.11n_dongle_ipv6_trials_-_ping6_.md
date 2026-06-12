---
title: "Atheros AR9271 802.11n dongle: ipv6 trials - ping6 not working"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by vkbidve on 2014-11-04
Hi,

I am using ubuntu 14.04 LTS linux box. I am working on a project where Link Local networking with IPv6 is needed without using DHCPv6.

I am using Atheros AR9271 wifi usb dongle (mfg by TP-Link) to get wifi connectivity and trying to get it work on IPv6. Here are some steps I performed and their outcomes:

**1.** I plugged in two dongles in two PCs and clicked on 'Edit Connections' option appearing in the network icon in the task bar to configure its settings. In this, I went to the Wi-Fi tab first and set some SSID, 'Infrastructure' networking mode, MAC adrs shown automatically, and then I went to 'IPv4 Settings' tab. In that, I set the 'method' to 'Disabled'. Then I went to IPv6 Settings tab, where I set the 'method' to 'Link Local Only' and then saved the settings. This was repeated on both PCs with both dongles. 

Then I used "ping6 -I wlan0 <ipv6_address_of_other_end>" command and it pings happily. This happens from both ends.

**2.** Then I used ubuntu's built-in 'Settings->Network' dialog-box to configure one wifi dongle as 'Wi-Fi Hotspot' and another one to connect to the network created by first one. They connect with each other. The ping6 command also pings happily from both ends.

**3.** Then I went to terminal. Ran the commands "ip addr flush dev wlan0" to remove all ip addresses assigned till now and then "ip -6 addr add <ipv6_link_local_address_calculated_from_mac_id>" to assign only ipv6 link local address, which was exactly same as before. This was repeated on both ends. The command "ifconfig wlan0" also confirmed the ipv6 addresses assigned. Then I ran "ifup wlan0" on both ends and a ping6 command same as before. Now I got response "connect: Network is unreachable". It didn't ping. 

After this, I repeated the same steps on wired ethernet connection till step "3" above (of course, by replacing wlan0 with eth0) and it pinged the other end even in step 3 above.

Now, my question is, does it need anything extra to get a wi-fi connection working at link-local scope? Which thing am I missing in this?

Thanks and Regards

Vasudeo

---

### Post by vkbidve on 2014-11-05
Any suggestions/hints?

---

### Post by vkbidve on 2014-11-07
Here is a point of difference I spotted:

When I try above steps without making the wifi interface a 'hotspot' I get following output from "ifconfig wlan2" command:

[FONT=courier new]wlan2     Link encap:Ethernet  HWaddr e8:de:27:0f:68:62  
             UP BROADCAST MULTICAST  MTU:1500  Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000 
             RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/FONT]
But when I configure it as a hotspot, then I get following output for the same:

[FONT=courier new]wlan2     Link encap:Ethernet  HWaddr e8:de:27:0f:68:62  
             inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
             inet6 addr: fe80::eade:27ff:fe0f:6862/64 Scope:Link
             UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000 
             RX bytes:0 (0.0 B)  TX bytes:11212 (11.2 KB)
[/FONT]

Apart from the IP addresses assigned, I see another difference is the word "RUNNING" in the status. So here is again my question rephrased:

1. Even if I add IP addresses using "ip addr add" command, the status shown doesn't have the word "RUNNING". So what happens internally with the interface, which sets it in "RUNNING" state? I am sure if I do *THE SAME* programmatically, it will work!
2. Why ethernet interfaces always show the status as "RUNNING" once turned up using "ip link set dev eth0 up" but why not the wifi interfaces?

Can somebody guide me to *THAT* piece of missing configuration?

---

