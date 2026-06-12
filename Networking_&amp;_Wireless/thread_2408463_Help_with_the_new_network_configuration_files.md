---
title: "Help with the new network configuration files?"
date: 2018-12-18
forum: Networking &amp; Wireless
---

### Post by Dubbayoo on 2018-12-18
Can someone explain or point me toward a dns howto for desktop Ubuntu? I'm on 18.04 and I cannot figure which method is being used. I have zero files in /etc/netplan. 

I ran: 

```

me@othello:/etc$ sudo netplan --debug apply
[sudo] password for me: (not my actual username)
DEBUG:no netplan generated networkd configuration exists
DEBUG:no netplan generated NM configuration exists
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets: {}
  vlans: {}
  wifis: {}

DEBUG:Skipping non-physical interface: lo
DEBUG:Skipping non-physical interface: eno1
DEBUG:Skipping non-physical interface: vmnet1
DEBUG:Skipping non-physical interface: vmnet8
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for eno1
DEBUG:netplan triggering .link rules for vmnet1
DEBUG:netplan triggering .link rules for vmnet8
```

-------------
I tried using the GUI (Network Mgr) and added an internal DNS server

```
steve@othello:/etc/netplan$ systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 4 (vmnet8)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 3 (vmnet1)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no

Link 2 (eno1)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 8.8.8.8
                      8.8.4.4
                      192.168.1.110
```
--------

That last DNS server is not actually being used in resolving. I desperately need that to change. I can telnet to it on port 53 so it's not a connectivity issue.  Where do I put that to put it into use?

---

### Post by QIII on 2018-12-18
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2408439").

Please do not hijack the threads of other users.

---

### Post by TheFu on 2018-12-18
Not sure if this other thread will help, but [https://ubuntuforums.org/showthread.php?t=2403929](https://ubuntuforums.org/showthread.php?t=2403929)  is all I found about 18.04 desktop configs.

Initially, I tried to find something that said only 2 DNS servers were allowed in 18.04. Didn't find that or anything about it.  Usually it is best to have the local DNS first in the list.

---

### Post by Dubbayoo on 2018-12-19
> **TheFu said:**
> Not sure if this other thread will help, but [https://ubuntuforums.org/showthread.php?t=2403929](https://ubuntuforums.org/showthread.php?t=2403929)  is all I found about 18.04 desktop configs.

Initially, I tried to find something that said only 2 DNS servers were allowed in 18.04. Didn't find that or anything about it.  Usually it is best to have the local DNS first in the list.

I'm fine trying that but what file do I edit to change w/o using NetworkManager GUI?

---

