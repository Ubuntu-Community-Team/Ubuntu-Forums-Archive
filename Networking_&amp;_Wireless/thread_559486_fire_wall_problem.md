---
title: "fire wall problem"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by markkeng on 2007-09-25
hey how do i remove my router firewall? it is very irritating i'm using a lynksys router. i cannot download any torrent eventhough i have already forwarded my ports and everything. please help. even before i used linux this keeps on happening..... this is crap....

---

### Post by dmizer on 2007-09-25
it may not be your router.  what client are you using for bittorrent?

---

### Post by markkeng on 2007-09-25
im using azureus but the default torrent doesnt work either thanks for helping:P

---

### Post by dmizer on 2007-09-25
okay ... couple of things then.  first of all, what's the output of:
ifconfig

and what model and version of linksys router do you have?

---

### Post by markkeng on 2007-09-25
i tried again just now it said that in azureus im firewalled but i dont have a firewall? right? then i tried the NAT?FIREWALL test and it said listening port 32489 (the port im using) ...OK!!! wth?

---

### Post by markkeng on 2007-09-25
just right now it said again that NAT..OK!! it keeps switching from firwealled to NAT...OK!! anyways here is the ifconfig


[/B]eth0      Link encap:Ethernet  HWaddr 00:0E:A6:41:82:A7  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe41:82a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48333756 (46.0 MiB)  TX bytes:4209045 (4.0 MiB)
          Interrupt:20 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6114 (5.9 KiB)  TX bytes:6114 (5.9 KiB)

---

### Post by markkeng on 2007-09-25
oh yeah im using linksys etherfast
cable/dsl router model no. BEFSR41

---

### Post by dmizer on 2007-09-25
okay ... first of all, disable ipv6:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

then reboot.

then install sun java:
[https://help.ubuntu.com/community/Java?highlight=%28java%29%7C%28sun%29#head-f4267cc37a197ccf46397cc58ff0944838741956](https://help.ubuntu.com/community/Java?highlight=%28java%29%7C%28sun%29#head-f4267cc37a197ccf46397cc58ff0944838741956)

and make sun java the default:
[https://help.ubuntu.com/community/Java?highlight=%28java%29%7C%28sun%29#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java?highlight=%28java%29%7C%28sun%29#head-fef9352fb26820bb774df978180c9dd3a60e777b)

restart azureus and try again.

---

### Post by markkeng on 2007-09-25
hahaha i'm sorry didnt quite understand how to install java hahaha please help again. sorry im quite dependent on you.

---

### Post by markkeng on 2007-09-25
Ubuntu 7.04

    *  Sun Java6: sun-java6-bin, sun-java6-jre
    *  Blackdown Java2 1.4: j2re1.4

 sudo apt-get install sun-java5-bin

is this right?

---

### Post by markkeng on 2007-09-25
well tried my best. got what it was trying to say but is still didnt work.... :(

---

### Post by markkeng on 2007-09-25
woohooo some how i managed to make it right hahaha. ubuntu is really complicated. i still have much to learn. but why is it that i only get 15-25kpbs per second when im downloading recent episodes that have a LOT of seeders and peers? my classmates get higher speeds than me... our internet cam from the same isp and same plan.... wat to do to improve this?

---

### Post by dmizer on 2007-09-27
> **markkeng said:**
> woohooo some how i managed to make it right hahaha. ubuntu is really complicated. i still have much to learn. but why is it that i only get 15-25kpbs per second when im downloading recent episodes that have a LOT of seeders and peers? my classmates get higher speeds than me... our internet cam from the same isp and same plan.... wat to do to improve this?

i don't know how to help you any more than what i've given you, but at least it's functional now.  from here, i would double check firewall settings: what port is forwarded, and does it match the port setting in azureus? does the ip address setting in your router match your ubuntu ip address?

here's lots more information: [http://azureuswiki.com/index.php/PortForwarding](http://azureuswiki.com/index.php/PortForwarding)

---

