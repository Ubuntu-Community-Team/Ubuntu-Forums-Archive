---
title: "Ubuntu 12.04 LTS wubi Amule 2.3.1 Kad firewalled and low ID!"
date: 2013-11-15
forum: Networking &amp; Wireless
---

### Post by gianboscom on 2013-11-15
Hello everybody!
[B]
What am I running?[/B] Ubuntu 12.04 LTS through wubi, and Amule 2.3.1; 7.7 GiB memory, Intel Core i5-2310 CPU, 64-bit, dual boot. 

**What is my problem?** My kad is firewalled, and I am receiving low ID! [COLOR=#0000ff](Please see attachments for kad and ed2k info)[/COLOR]

[ATTACH=CONFIG]247846[/ATTACH] [ATTACH=CONFIG]247847[/ATTACH][B]

**What do I need? **[/B]I would appreciate any help in getting  this sorted out. If there is something I am doing wrong or something I  am not doing please let me know! Any information you need just please  let me know. Thanks in advance![B]

What have I done?[/B]

[LIST]
[*]I opened tcp port 4662, and udp ports 4672 and 4665 in ufw: 
[/LIST]
 financialenterprises@ubuntu:~$ sudo ufw status verbose
[sudo] password for financialenterprises: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
4662/tcp                   ALLOW IN    192.168.0.13
4672/udp                   ALLOW IN    192.168.0.13
4665/udp                   ALLOW IN    192.168.0.13


[LIST]
[*]I opened tcp port 4662, and udp ports 4672 and 4775 in my router's configurations page [COLOR=#0000ff](please see attachment!)[/COLOR] 
[/LIST]

[ATTACH=CONFIG]247848[/ATTACH]

[LIST]
[*]Copied ifconfig -a: 
[/LIST]
 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 54:04:a6:8a:da:08  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe8a:da08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:963082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:745673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1003568304 (1.0 GB)  TX bytes:364717131 (364.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:655811 (655.8 KB)  TX bytes:655811 (655.8 KB)

---

### Post by gianboscom on 2013-11-18
does anyone have suggestions on what I can do to allow my kad to connect appropiately and get high ID?

---

### Post by gianboscom on 2013-11-22
is there some piece of information you guys need in order to help me solve the issue? does no one know anything about Amule?

---

