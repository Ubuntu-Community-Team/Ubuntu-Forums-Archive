---
title: "if-pre-up.d scripts not loaded"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by ridgerunner7 on 2008-07-21
I have my own iptables script. It works fine. I don't want to use UFW so I removed it.

I put my firewall script in /etc/network/if-pre-up.d/ but I have to manually run it every time I bring up the interface. It leaves my interface unprotected!

This used to work prior to hardy. I have a Dapper server where it's working fine. I cannot figure out where scripts in if-pre-up.d get run so I can't tell why prior distros worked where Hardy is not. 

Any suggestions?

---

### Post by ridgerunner7 on 2008-07-21
Oh and BTW the script is executable and yet iptables is wide open:

```
$ ls -l /etc/network/if-pre-up.d/
-rwxr-xr-x 1 root root 11899 2008-07-22 09:44 firewall
-rwxr-xr-x 1 root root  2358 2007-12-21 22:36 wireless-tools
lrwxrwxrwx 1 root root    32 2008-07-09 15:01 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh
$ sudo iptables -nvL
Chain INPUT (policy ACCEPT 239 packets, 18184 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 153 packets, 17002 bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

---

### Post by andersja on 2009-11-30
I have a similar problem - I added a simple script to if-pre-up.d to do an iwconfig rate setting upon connection, but the rate can later be observed as exceeding the rate I capped it at, so I must assume the script was not run. 

Anyone got any indications on how to troubleshoot this?

---

