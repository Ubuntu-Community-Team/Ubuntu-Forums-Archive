---
title: "what DNS servers did my DHCP server give me?"
date: 2018-08-31
forum: Networking &amp; Wireless
---

### Post by swilson2 on 2018-08-31
I'm running the server version of ubuntu 18.04.  From a fresh install how do I find out what DNS servers I'm using?  The /etc/resolv.conf only shows 127.0.0.53.  

In the olden days, you used to use 'nmcli' to find out what DNS servers got pushed down to you.  It appears NetworkManager is not installed by default any more.  What is the standard practice now?

---

### Post by chili555 on 2018-08-31
Please try:```
sudo systemd-resolve --status
```On my system, it shows (redacted):```
Link 3 (wlp3s0)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
 DNSSEC supported: no
         [COLOR="#FF0000"]DNS Servers[/COLOR]: 8.8.8.8
                      8.8.4.4
                      2600:1700:5aa0:830::1

```

---

### Post by swilson2 on 2018-08-31
Yep that's what I was looking for.

also:

[COLOR=#242729][FONT=Consolas]cat /run/systemd/netif/leases/2

[/FONT][/COLOR]Shows all network info

---

