---
title: "no internet after latest update"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by dieuwke on 2014-01-30
Hi everyone,

I have an Asus Zenbook, and after the latest update (I use Ubuntu 13.10) my internet stopped working (both wifi and cable). It says I am connected and I can ping myself, but I cannot open any website. If I boot on Windows the internet does work. I have tried several older kernels, but none of them solves the problem. Previous posts about somewhat similar issues could not help me either. I really don't know what to do anymore! Any help would be appreciated! (I would be of course happy to post any additional information that would help solve the problem).

Thanks in advance!

---

### Post by Ubi_one_2014 on 2014-01-30
did you reboot after the update

otherwise, try remove the cache of your browser

---

### Post by dieuwke on 2014-01-30
I have rebooted several times (to check windows boot, and to try different kernels) but that did not work. Removing the cache doesn't work either. I don't think it is a browser problem, because I cannot update/upgrade anymore either.

---

### Post by ian-weisser on 2014-01-30
What were the updates?
You can find the list of updates, and when they were done, in /var/log/apt/history.log

You say you can ping yourself.
Can you ping other machines on your LAN?
Can you ping your upstream router?
Can you ping any servers on the internet?

---

### Post by dieuwke on 2014-01-30
I can ping other machines on my network, but I can't ping other servers. I am not sure how I should ping an upstream router.

In the latest updates I find nothing the following things: upgrade: mysql-server-core-5.5, mysql-client-core5.5, mysql:-common, libmysqlclient18 and a bunch of vlc things (nox, plugin-notify, plugin-pulse data..).

Of course I am not even sure if it is related to this update..

---

### Post by ian-weisser on 2014-01-30
If you can ping other machines on your local network, then it seems like Ubuntu's networking is functioning.
Check your router or gateway.

---

### Post by dieuwke on 2014-01-30
doesn't this contradict the fact that it works when I run windows on my machines (and that it works on other machines)?

---

### Post by ian-weisser on 2014-01-30
Please show us the contents of an example non-working connection file in /etc/NetworkManager/system-connections

---

### Post by dieuwke on 2014-01-31
sudo cat /etc/NetworkManager/system-connections/UPC1386
[connection]
id=UPC1386581
uuid=b148f2d1-61d-4023-bab8-3a65d01d32ff
type=802-11-wireless

[802-11-wireless]
ssid=UPC1386581
mode=infrastructure
mac-address=C4:85:08:02:48:D9
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
auth-alg=open
psk=******

[ipv4]
method=auto

[ip6]
method=auto


However, my computer says that the connection is there, I just cannot use it. (Not only in the browser, also not to update). Does this help?

---

### Post by ian-weisser on 2014-01-31
I don't see anything wrong with your network settings, and you mentioned that you do connect (receive a dhcp address from your router), and that pinging within the LAN does work. It sure looks like nothing is wrong on the Ubuntu side.

Let's check the Ubuntu firewall settings:
```
sudo iptables -L
```

For comparison, here's what mine look like:
```
$ sudo iptables -L
[sudo] password for ian: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```
If you look carefully, there are no rules at all, and everything is set to ACCEPT. That's the default in Ubuntu. Clearly my firewall blocks nothing. My router's firewall, on the other hand, blocks almost everything.

---

### Post by dieuwke on 2014-01-31
My output is exactly the same.

---

### Post by ian-weisser on 2014-01-31
Open a terminal and try the 'traceroute' command.

First, try tracerouting your router.
```
$ traceroute 192.168.0.1                                      # Use the IP address of YOUR router, not mine.
traceroute to 192.168.0.1 (192.168.0.1), 30 hops max, 60 byte packets
 1  192.168.0.1 (192.168.0.1)  1.207 ms  2.520 ms  2.934 ms
```

Next, try tracing a public internet server.
```
$ traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.0.1 (192.168.0.1)  1.311 ms  2.465 ms  2.911 ms
 2  adsl-108-199-221-254.dsl.milwwi.sbcglobal.net (108.199.221.254)  14.281 ms  16.152 ms  20.200 ms
 3  dist2-vlan50.milwwi.ameritech.net (65.43.19.227)  21.324 ms  23.639 ms  26.062 ms
 4  bb2-10g9-0-0.milwwi.sbcglobal.net (151.164.103.138)  28.602 ms  31.030 ms  32.972 ms
 5  ggr3.cgcil.ip.att.net (12.122.133.9)  37.864 ms  40.690 ms  42.624 ms
 6  * * *
 7  209.85.254.128 (209.85.254.128)  16.624 ms  33.863 ms 209.85.254.120 (209.85.254.120)  31.364 ms
 8  209.85.254.240 (209.85.254.240)  25.308 ms 72.14.237.130 (72.14.237.130)  27.100 ms 72.14.237.133 (72.14.237.133)  29.462 ms
 9  72.14.238.104 (72.14.238.104)  49.300 ms 209.85.248.228 (209.85.248.228)  44.753 ms 72.14.238.106 (72.14.238.106)  49.291 ms
10  216.239.46.191 (216.239.46.191)  51.455 ms  53.321 ms 216.239.43.217 (216.239.43.217)  60.768 ms
11  * * *
12  google-public-dns-a.google.com (8.8.8.8)  40.781 ms  41.939 ms  43.637 ms
```

---

### Post by dieuwke on 2014-02-01
I don't have the 'traceroute' installed, and I can't, because I have no internet... :s.
Yesterday when I was at the university, all of a sudden the internet worked for a while. Later in a cafe it did not anymore, and at home it doesn't either. Does this give extra information?

---

### Post by ian-weisser on 2014-02-01
Traceroute is included with the default install of every flavor of Ubuntu. Several other handy networking tools, including traceroute, are included with the ubuntu-standard metapackage at install specifically to help diagnose network problems.

Do you have a standard flavor of *buntu 13.10 installed? Or did you roll-your-own?

---

### Post by dieuwke on 2014-02-01
I think it is a standard one (I did not do a clean install but upgraded from 13.10). I believe it is in a standard repository, but I am pretty sure it is not installed on my machine.. I think I'll just try to reinstall ubuntu, and see if that helps

---

