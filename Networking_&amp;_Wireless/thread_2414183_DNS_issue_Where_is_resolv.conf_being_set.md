---
title: "DNS issue: Where is resolv.conf being set?"
date: 2019-03-06
forum: Networking &amp; Wireless
---

### Post by jonathanese on 2019-03-06
I've been having issues with name resolution after an update from 18.04 to 18.10 threw off some of my network settings.

After tracing the issue around, I found that if I write **nameserver 8.8.8.8** directly to /etc/resolv.conf, it resolves the issue until next bootup. The problem is that I can't figure out what service/setting is overwriting resolv.conf back to 127.0.0.1

- I've checked /etc/resolvconf/resolv.conf.d/base, but I already have **nameserver 8.8.8.8** entered in there.
- The header in resolv.conf mentions changes should be made related to systemd-resolve, but I receive the error: [B]Failed to get global data: Unit dbus-org.freedesktop.resolve1.service not found.

[/B]As a further note, I am running PiHole, which is basically a wrapper for dnsmasq which pulls lists of known bad IP addresses (ads, spam, etc) and blocks them from name resolution. It works as your network's DNS server and thus allows you to configure forward DNS query addresses. (You can configure multiple and it will choose the fastest). This MAY be overriding or conflicting with another process that is normally disabled by pihole, but re-enabled during the update. My next step there is to try reinstalling PiHole to see if it configures things back.

Do you guys know a way to figure out what is currently sourcing my list of nameservers? (Or for that matter, a way to clean up redundant junk from other services and files trying to perform the same task?)

---

### Post by jonathanese on 2019-03-06
Here are some statuses:
**service dnsmasq status**: Inactive (dead) 
**service pihole-FTL status**:  Not running. dnsmasq: cannot access /etc/dnsmasq.d/lxd: no such file or directory

These two seem to point to an issue with dnsmasq. So I may try reinstalling dnsmasq, but I'm not sure if 18.10 changed a dns resolution service or something that would break if I tried reinstalling dnsmasq.

[Update]
So resolv.conf seems to be overwritten by netplan. When I run **netplan apply** it reverts resolv.conf back to 127.0.0.1. If I change it back to 8.8.8.8 after this, it takes a long time but fails resolution. Interesting, because 8.8.8.8 is my DNS address configured in netplan.

---

### Post by jonathanese on 2019-03-06
OK so I ran netplan apply with the debug flag set. Let me know what looks off.

```
root@gammaserver:/etc/systemd# netplan --debug apply** (generate:20048): DEBUG: 22:50:00.425: Processing input file /etc/netplan/config.yaml..
** (generate:20048): DEBUG: 22:50:00.425: starting new processing pass
** (generate:20048): DEBUG: 22:50:00.426: enp3s0: setting default backend to 1
** (generate:20048): DEBUG: 22:50:00.426: Generating output files..
** (generate:20048): DEBUG: 22:50:00.426: NetworkManager: definition enp3s0 is not for us (backend 1)
(generate:20048): GLib-DEBUG: 22:50:00.426: posix_spawn avoided (fd close requested)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:enp3s0 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    enp3s0:
      addresses:
      - 192.168.1.1/24
      dhcp4: false
      nameservers:
        addresses:
        - 8.8.8.8
        - 8.8.4.4
      optional: false
  vlans: {}
  wifis: {}



```

---

### Post by pcfan1234 on 2019-03-07
18.04/18.10 uses systemd-resolve. Do not edit /etc/resolv.conf
Show```
system-resolve --status
```
```
nslookup heise.de 127.0.0.53
```
```
ls -la /etc/resolv.conf 
```
systemd-resolve uses 127.0.0.53

---

### Post by jonathanese on 2019-03-07
> [COLOR=#000000]Do not edit /etc/resolv.conf[/COLOR]

I hear this a ton, and it confuses me. It's more like "do not edit unless you are prepared for the fact that it will be overwritten at boot or network restart", which is little more than an inconvenience, not some heavy system-breaking mistake as people make it out to be.

Sorry, that's not directed at you, it's just a rant at hearing that phrase a lot.


I'll send you the result of system-resolve --status when I get home tonight.

last I ran ls -la /etc/resolv.conf, it gave me:

```
lrwxrwxrwx 1 root root 27 Mar  3 02:54 /etc/resolv.conf -> /run/resolvconf/resolv.conf
```
I could run this again tonight as well, but I don't think it had actually changed. I still have my network renderer set to networkd in netplan. (Note that I'm using Ubuntu server)

The 127.0.0.53 bit is new info to to me so I'll have to look into it. But I'll get you that info as well.

---

### Post by jonathanese on 2019-03-07
OK I'm back with resultssssss

systemd-resolve --status

```
Global       LLMNR setting: no
MulticastDNS setting: no
  DNSOverTLS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
  Current DNS Server: 8.8.8.8
         DNS Servers: 8.8.8.8
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

```


nslookup heise.de 127.0.0.53
```
Server:         127.0.0.53Address:        127.0.0.53#53


Non-authoritative answer:
Name:   heise.de
Address: 193.99.144.80
Name:   heise.de
Address: 2a02:2e0:3fe:1001:302::



```

ls -la /etc/resolv.conf
```
lrwxrwxrwx 1 root root 29 Mar  3 19:49 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
```

---

