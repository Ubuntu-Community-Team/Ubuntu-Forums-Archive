---
title: "GAVE UP (Ubuntu 16.04 and problem with rtl8812au driver)"
date: 2016-12-02
forum: Networking &amp; Wireless
---

### Post by bijan2 on 2016-12-02
Using Ubuntu 16.04 driver** (rtl8812au-dkms**) causes USB AC Wireless dongle drops connection frequently. Have anyone experienced this or my Hardware has gone bad? Appreciate any help.
TIA

---

### Post by wildmanne39 on 2016-12-02
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by bijan2 on 2016-12-03
Thanks for your reply. For now I have un-installed the Ubuntu driver and compiled rtl8812AU_8821AU_linux from git hub. Things are much better. I will report again with Wireless Script if problem exist.

---

### Post by wildmanne39 on 2016-12-03
That is what my suggestion was going to be after I reviewed the information and possibly to change some of your network settings.

---

### Post by bijan2 on 2016-12-05
After testing several Github drivers for rtl8812au they all have their issues and unfortunately none of them stays connected as you wish. The Wireless USB dongle works good on Windows 10.
Here are some stats that Ubuntu 16.04 driver drops packets and causes connection issues:

bijan@U56E:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether c8:60:00:33:c1:a8 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 40:25:c2:bf:96:c8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.148/24 brd 192.168.1.255 scope global dynamic wlp2s0
       valid_lft 81875sec preferred_lft 81875sec
    inet6 2601:601:4100:9283::1014/128 scope global dynamic 
       valid_lft 2990sec preferred_lft 2690sec
    inet6 fe80::c8a2:f783:91dc:ef77/64 scope link 
       valid_lft forever preferred_lft forever
5: enx8416f909ff85: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 84:16:f9:09:ff:85 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.157/24 brd 192.168.1.255 scope global dynamic enx8416f909ff85
       valid_lft 84166sec preferred_lft 84166sec
    inet6 2601:601:4100:9283::1015/128 scope global dynamic 
       valid_lft 84904sec preferred_lft 84904sec
    inet6 fe80::c604:3dee:d4a9:d1a/64 scope link 
       valid_lft forever preferred_lft forever


===========================================================


Showing (5: ) USB Wireless Adaptor (rtl8812au Ubuntu driver) specific Network interface Statistics. Notice packets dropped for unknown reason causing connection loss.


bijan@U56E:~$ ip -s link ls enx8416f909ff85
5: enx8416f909ff85: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 84:16:f9:09:ff:85 brd ff:ff:ff:ff:ff:ff
    RX: bytes  packets  errors  dropped overrun mcast   
    2732981    3945     0       63      0       0       
    TX: bytes  packets  errors  dropped carrier collsns 
    1059385    5026     0       44      0       0


Hope this issue get resolved on the next release of Ubuntu or perhaps sooner.
Thank you,

---

### Post by wildmanne39 on 2016-12-05
Please see post 2.

---

### Post by bijan2 on 2016-12-13
Unfortunately Ubuntu still struggling with their Wireless configurations. Developers should look at this issue more seriously and come up with a couple of good working drivers. I just marked this thread as Solved but in reality the problem still there and it is a **BIG** one. Good luck on getting the developers attentions for reworking few of those WiFi Drivers..
Thank you,

---

### Post by jeremy31 on 2016-12-13
Please don't mark a thread solved that isn't.  There are parameters for the 8812au module that may help.  We might be able to help if you post results from the wireless script

I have the rtl8812au-dkms installed even though I don't have the device as I was troubleshooting DKMS issues with the module as it seems the source code in the dkms.conf file will build the module against the old kernel source instead of the new kernel.  A couple parameters of interest for this module are:
rtw_enusbss
rtw_power_mgnt

---

### Post by bijan2 on 2016-12-13
I am sorry that I marked this thread Solved. I wish there was an _Unresolved_ option. The fact is the problem still exist and needs serious attention. Are there are any functional WiFi Drivers you can recommend? 
Thank you

---

### Post by wildmanne39 on 2016-12-13
We recommend you post the information that was asked for by jeremy31 and myself several days ago.

---

### Post by bijan2 on 2016-12-13
I am sorry, I did return the USB adapter back to Amazon once I found out there was no "working" Linux Driver for it. That is why I did not follow with the wireless script.

---

### Post by jeremy31 on 2016-12-13
You might want to use thread tools to unmark as solved and edit the topic of the original post to add "gave up"

---

