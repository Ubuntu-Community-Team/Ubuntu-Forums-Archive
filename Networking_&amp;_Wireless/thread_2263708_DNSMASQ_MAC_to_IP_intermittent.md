---
title: "DNSMASQ MAC to IP intermittent"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by ripeart on 2015-02-02
Hi,

So I have one host that it's not working on. I have tried all different combinations of formatting the MAC address and am curious if I am missing something. I know the section is working as I have changed IPs for a couple MACs, restarted dnsmasq service and renewed IP and the new IP was granted. Here's my dnsmasq.conf:  Any thoughts? I'm having trouble specifically with pibr.[INDENT][FONT=courier new]
[FONT=lucida console]interface=wlan0[/FONT][/FONT][/INDENT]
[INDENT][FONT=lucida console]expand-hosts[/FONT][/INDENT]
[INDENT][FONT=lucida console]dhcp-range=192.168.168.20,192.168.168.99,24h[/FONT][/INDENT]
[INDENT][FONT=lucida console]dhcp-host=98-FC-11-FC-68-8E,ts200v,192.168.168.100,infinite[/FONT][/INDENT]
[INDENT][FONT=lucida console]dhcp-host=38:b1:db:31:f9:65,lrcbox,192.168.168.101,infinite[/FONT][/INDENT]
[INDENT][FONT=lucida console]dhcp-host=00:24:a5:47:de:a2,buffalo,192.168.168.103,infinite[/FONT][/INDENT]
[INDENT][FONT=lucida console]dhcp-host=00:0f:60:02:f1:c3,pibr,192.168.168.104,infinite[/FONT][/INDENT]
[INDENT][FONT=lucida console]dhcp-option=3,192.168.168.2[/FONT][/INDENT]
[INDENT][FONT=lucida console]dhcp-option=42,0.0.0.0[/FONT][/INDENT]

---

