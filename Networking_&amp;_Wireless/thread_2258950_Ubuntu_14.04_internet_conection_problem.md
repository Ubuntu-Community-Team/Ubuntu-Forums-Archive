---
title: "Ubuntu 14.04 internet conection problem"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by Rasel_Khan on 2014-12-31
Hello

I've installed Ubuntu 14.04 and with wired(Broadband) pppo connection setup, showing me connection is ok and with skype is online but i can't browser connection, only allow for google search (Chrome Browser ) but can't access main sites, Terminal, Ubuntu Software Center via internet, When browse any site by Firefox then showing me server not found message, Any one tell me how i can fix this ?

When  I type this command (ifconfig -a) then showing me message by terminal , see below

```
Rasel Khan:~ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e0:69:95:12:b0:4c  
          inet6 addr: fe80::e269:95ff:fe12:b04c/64 Scope:Link
          inet6 addr: fec0::b:7d91:52bc:99b8:bbed/64 Scope:Site
          inet6 addr: 2002:67e4:389:b:7d91:52bc:99b8:bbed/64 Scope:Global
          inet6 addr: fec0::b:e269:95ff:fe12:b04c/64 Scope:Site
          inet6 addr: 2002:67e4:389:b:e269:95ff:fe12:b04c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130198 errors:0 dropped:275 overruns:0 frame:0
          TX packets:14638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12294924 (12.2 MB)  TX bytes:1911627 (1.9 MB)
          Interrupt:20 Memory:fe400000-fe420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:209887 (209.8 KB)  TX bytes:209887 (209.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.16.64.157  P-t-P:172.16.0.0  Mask:255.255.255.255
          inet6 addr: fe80::c941:650f:c729:a174/10 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:13061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4222533 (4.2 MB)  TX bytes:1518630 (1.5 MB)
```

---

### Post by praseodym on 2014-12-31
Please run the wireless script from the sticky thread and show the outputs. Also deactivate IPv6 in the network-manager profile settings

---

### Post by Rasel_Khan on 2014-12-31
How? Give me instruction manually @praseodym

---

### Post by praseodym on 2014-12-31
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
The command will download a script and create a file named (wireless-info.txt or wireless-info.txt.tar.gz) depending on the size of the file. It will be placed in your home folder.

---

### Post by Rasel_Khan on 2015-01-18
Still not working @[ 						 							[IMG]http://ubuntuforums.org/images/avatars/UF_Logo_original_90.png[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1411497") 				 				 					 						 	[**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497")

---

### Post by praseodym on 2015-01-18
Please show the output (diagnosis script)

---

