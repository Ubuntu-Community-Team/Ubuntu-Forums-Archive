---
title: "DNS not working on ubuntu 19.04"
date: 2019-10-21
forum: Networking &amp; Wireless
---

### Post by mdsikir on 2019-10-21
I have a DNS problem that is bugging me for a long time.
Here is what happens:

1) First **ping 8.8.8.8 **works correctly but **links [www.slashdot.org]("http://www.slashdot.org") **does not. So, it is really a DNS problem.

2) accessing to the specific server works, that is **nslookup yahoo.com 8.8.8.8 **works correctly.

3) The DNS appears to work with[INDENT]mathieu@kotohira:~$ journalctl -u systemd-resolved -f[/INDENT]
[INDENT]-- Logs begin at Sat 2018-05-19 16:09:37 CEST. --[/INDENT]
[INDENT]lis 21 10:50:23 kotohira systemd[1]: Stopping Network Name Resolution...[/INDENT]
[INDENT]lis 21 10:50:23 kotohira systemd[1]: systemd-resolved.service: Succeeded.[/INDENT]
[INDENT]lis 21 10:50:23 kotohira systemd[1]: Stopped Network Name Resolution.[/INDENT]
[INDENT]-- Reboot --[/INDENT]
[INDENT]lis 21 10:51:20 kotohira systemd[1]: Starting Network Name Resolution...[/INDENT]
[INDENT]lis 21 10:51:21 kotohira systemd-resolved[857]: Positive Trust Anchors:[/INDENT]
[INDENT]lis 21 10:51:21 kotohira systemd-resolved[857]: . IN DS 19036 8 2 49aac11d7b6f6446702e54a1607371607a1a41855200fd2ce1cdde32f24e8fb5[/INDENT]
[INDENT]lis 21 10:51:21 kotohira systemd-resolved[857]: . IN DS 20326 8 2 e06d44b80b8f1d39a95c0b0d7c65d08458e880409bbc683457104237c7f8ec8d[/INDENT]
[INDENT]lis 21 10:51:21 kotohira systemd-resolved[857]: Negative trust anchors: 10.in-addr.arpa 16.172.in-addr.arpa 17.172.in-addr.arpa 18.172.in-addr.arpa 19.172.in-addr.arpa 20.172.in-addr.arpa 21.172.in-addr.arpa 22.172.in-addr.arpa 23.172.in-addr.arpa 24.172.in-addr.arpa 25.172.in-addr.arpa 26.172.in-addr.arpa 27.172.in-addr.arpa 28.172.in-addr.arpa 29.172.in-addr.arpa 30.172.in-addr.arpa 31.172.in-addr.arpa 168.192.in-addr.arpa d.f.ip6.arpa corp home internal intranet lan local private test[/INDENT]
[INDENT]lis 21 10:51:21 kotohira systemd-resolved[857]: Using system hostname 'kotohira'.[/INDENT]
[INDENT]lis 21 10:51:21 kotohira systemd[1]: Started Network Name Resolution.
[/INDENT]

4) the result of **systemd-resolve --status** is 

[INDENT]Global[/INDENT]
[INDENT]       LLMNR setting: no[/INDENT]
[INDENT]MulticastDNS setting: no[/INDENT]
[INDENT]  DNSOverTLS setting: no[/INDENT]
[INDENT]      DNSSEC setting: no[/INDENT]
[INDENT]    DNSSEC supported: no[/INDENT]
[INDENT]          DNSSEC NTA: 10.in-addr.arpa[/INDENT]
[INDENT]                      16.172.in-addr.arpa[/INDENT]
[INDENT]                      168.192.in-addr.arpa[/INDENT]
[INDENT]                      17.172.in-addr.arpa[/INDENT]
[INDENT]                      18.172.in-addr.arpa[/INDENT]
[INDENT]                      19.172.in-addr.arpa[/INDENT]
[INDENT]                      20.172.in-addr.arpa[/INDENT]
[INDENT]                      21.172.in-addr.arpa[/INDENT]
[INDENT]                      22.172.in-addr.arpa[/INDENT]
[INDENT]                      23.172.in-addr.arpa[/INDENT]
[INDENT]                      24.172.in-addr.arpa[/INDENT]
[INDENT]                      25.172.in-addr.arpa[/INDENT]
[INDENT]                      26.172.in-addr.arpa[/INDENT]
[INDENT]                      27.172.in-addr.arpa[/INDENT]
[INDENT]                      28.172.in-addr.arpa[/INDENT]
[INDENT]                      29.172.in-addr.arpa[/INDENT]
[INDENT]                      30.172.in-addr.arpa[/INDENT]
[INDENT]                      31.172.in-addr.arpa[/INDENT]
[INDENT]                      corp[/INDENT]
[INDENT]                      d.f.ip6.arpa[/INDENT]
[INDENT]                      home[/INDENT]
[INDENT]                      internal[/INDENT]
[INDENT]                      intranet[/INDENT]
[INDENT]                      lan[/INDENT]
[INDENT]                      local[/INDENT]
[INDENT]                      private[/INDENT]
[INDENT]                      test[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Link 4 (br-c20ac0e23c54)[/INDENT]
[INDENT]      Current Scopes: none[/INDENT]
[INDENT]DefaultRoute setting: no[/INDENT]
[INDENT]       LLMNR setting: yes[/INDENT]
[INDENT]MulticastDNS setting: no[/INDENT]
[INDENT]  DNSOverTLS setting: no[/INDENT]
[INDENT]      DNSSEC setting: no[/INDENT]
[INDENT]    DNSSEC supported: no[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Link 3 (docker0)[/INDENT]
[INDENT]      Current Scopes: none[/INDENT]
[INDENT]DefaultRoute setting: no[/INDENT]
[INDENT]       LLMNR setting: yes[/INDENT]
[INDENT]MulticastDNS setting: no[/INDENT]
[INDENT]  DNSOverTLS setting: no[/INDENT]
[INDENT]      DNSSEC setting: no[/INDENT]
[INDENT]    DNSSEC supported: no[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Link 2 (eno1)[/INDENT]
[INDENT]      Current Scopes: DNS[/INDENT]
[INDENT]DefaultRoute setting: yes[/INDENT]
[INDENT]       LLMNR setting: yes[/INDENT]
[INDENT]MulticastDNS setting: no[/INDENT]
[INDENT]  DNSOverTLS setting: no[/INDENT]
[INDENT]      DNSSEC setting: no[/INDENT]
[INDENT]    DNSSEC supported: no[/INDENT]
[INDENT]  Current DNS Server: 8.8.8.8[/INDENT]
[INDENT]         DNS Servers: 8.8.8.8[/INDENT]
[INDENT]          DNS Domain: ~.[/INDENT]



Thus the server **8.8.8.8** is well indicated in the config.
Of course the DNS Domain is empty and this is a problem. But
a) I do not know what it is useful for.
b) I do not know how to set it as a google search returns plenty of bad hits.
c) It is not sure that setting it up would correct the problem

My questions:
1) How can I get detailed info on what goes wrong? **nslookup -debug yahoo.com**
does not show anything useful.
2) How to resolve the problem?
3) How to setup the **DNS Domain**? (I know what value it should be from another
computer on the same network that works correctly).

---

### Post by chili555 on 2019-10-21
Slashdot appears to have been off-line earlier today but seems to be working correctly now. Is it working for you?

Do you have other examples besides Slashdot?

---

