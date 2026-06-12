---
title: "Ubuntu Server 22.04 no systemd-resolved command"
date: 2022-06-22
forum: Networking &amp; Wireless
---

### Post by windofkeltia on 2022-06-22
I'm trying to set up static IP using [FONT=Courier New]netplan[/FONT]. In many places, _to discover the gateway_ to set for [FONT=Courier New]routes: ... via: <address>[/FONT], I'm advised to do:

[INDENT][/INDENT][FONT=Courier New]# systemd-resolved --status | grep Current[/FONT]

I have also tried "resolve" in place of "resolved" as posters use different spellings. However, no matter what the spelling, I'm told:

[INDENT][/INDENT][FONT=Courier New]systemd-resolved: command not found
[/FONT]
Thanks for any thoughts on this or on a reliable way to coax the system to reveal the gateway address to me.

---

### Post by TheFu on 2022-06-23
If you want the gateway to be automatically determined, you'll need to use DHCP.  That's a bad idea on a server, IMHO.  

There are other opinions on this subject and entire enterprises use DHCP to provide networking information for their servers. I know the appeal, but I've also seen a 100K+ employee company have all their DHCP servers disappear over time, before anyone noticed a bad DHCP setting.

As a result of that fault, all their static servers are manually configured with IPs, gateways, netmasks for each interface.

A quick command to get the existing gateway is:
```
$ echo $(read -r x x i x< <(ip r g 1);echo "$i")
```

But that isn't part of setting the nameservers.  The entire point of systemd-resolved (is is "resolved") is to create /etc/resolv.conf.  That's it. Nothing more.  So, we don't need systemd-resolved or resolvconf tools unless the nameservers can change.  On servers, this would be extremely odd.  So, we can "mask" both systemd-resolved and resolvconf, delete the symlink for  /etc/resolv.conf, then put the 2 nameserver lines into a new file, /etc/resolv.conf like we did for 15 yrs before either of those things existed.

In a mixed OS network, cough, if there are non-Unix OSes, then you might want some other settings in resolv.conf to use other types of name resolution/lookups.  Don't forget to be consistent with the /etc/nsswitch.conf file settings too.  Order matters in that file. For the hosts line:
```
hosts:          files dns
```
is the minimal, but there might be reasons to add other options.  I'm a puirist.  Local /etc/hosts and DNS. Nothing else.  There are different opinions about this too. ;)

---

### Post by chili555 on 2022-06-23
Please try:

```
sudo service systemd-resolved status
man systemd-resolved
```

---

