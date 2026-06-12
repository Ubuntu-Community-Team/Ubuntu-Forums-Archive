---
title: "KDE Connect Problems"
date: 2019-03-27
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2019-03-27
Every day for the past three days after I log on I get a drop down error.  It states.  "GSConnect:  Network error.  Error binding to address.  Address already in use."

I take it this has something to do with my installation of KDE Connect which I did three days ago and have been getting the error for three days.  At the bottom of the error it has something about info.  When I click it it opens a Gifthub page.  I scroll down to "Netwok error" and click on it, but nothing opens.  Can anyone give me any jhelp on this.  Oh yeah, I couldn't get my LG G7 Thinqu and Ubuntu 18.04 connected.

---

### Post by shane_faulkinbury2 on 2019-03-28
Anybody?  :confused:

---

### Post by SeijiSensei on 2019-03-28
I've had zero issues with KDEConnect myself.  Usually "cannot bind to address" means something else is already listening on that "port" number. A second instance of KDEConnect that you didn't know was running?  What does "ps aux" and "lsof" show? Do you see another, perhaps defunct, KDEConnect?  It uses randomly-selected ports between 1714 and 1764.  Both TCP and UDP are used.  Make sure you don't have any other software which uses ports in that range.

[https://community.kde.org/KDEConnect#I_have_two_devices_running_KDE_Connect_on_the_same_network.2C_but_they_can.27t_see_each_other](https://community.kde.org/KDEConnect#I_have_two_devices_running_KDE_Connect_on_the_same_network.2C_but_they_can.27t_see_each_other)

---

### Post by shane_faulkinbury2 on 2019-03-29
What if I'm on a VPN?

---

### Post by SeijiSensei on 2019-03-29
KDEConnect assumes that the phone and the computers it connects to are all in the same IP address space. If the phone has an address not in the same subnet as the computers, I don't think KDEConnect will work. You might be able to get around this with masquerading via iptables.

---

### Post by shane_faulkinbury2 on 2019-03-29
Her's what ip a gives me.```
ip a1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 80:c1:6e:eb:5f:d9 brd ff:ff:ff:ff:ff:ff
4: wlx24050fd8df9f: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 24:05:0f:d8:df:9f brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.145/24 brd 192.168.1.255 scope global dynamic noprefixroute wlx24050fd8df9f
       valid_lft 84746sec preferred_lft 84746sec
    inet6 fd33:d325:2b78:0:28a7:e8d:20f6:2383/64 scope global temporary dynamic 
       valid_lft 6917sec preferred_lft 3317sec
    inet6 fd33:d325:2b78:0:312d:13b8:9b1a:feb2/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 6917sec preferred_lft 3317sec
    inet6 fe80::198f:dc8c:895b:6da6/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
7: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.50.10.6 peer 10.50.10.5/32 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::7f2e:fea9:704d:34d4/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever
```

I don't see an "[COLOR=#DD0055][FONT=&quot]enp0s3" [SIZE=2]line.[/SIZE][/FONT][/COLOR]


The vpn on my mobile I shut off for the KDE Connect app.

---

### Post by SeijiSensei on 2019-03-30
Names change. The wireless adapter has that long name starting with "wlx."

---

### Post by shane_faulkinbury2 on 2019-03-30
So it's [COLOR=#000000][FONT=&quot]192.168.1.145?

[/FONT][/COLOR]

---

### Post by shane_faulkinbury2 on 2019-03-31
I plugged it manually in on my mobile and refreshed KDE on my computer and still see nothing.

---

