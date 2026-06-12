---
title: "Very weird problem"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by wquatan on 2006-09-19
Hi,

I have the following configuration :

LAN<-->IPCOP<-->SMC7404BRA(router)<-->Provider

The SMC gets a dynamic IP from the provider, has DNS incoporated and DHCP active (192....)
The IPCOP gets a dynamic IP from SMC, has DNS and DHCP active (10....)
Computers on LAN get a dynamic IP from IPCOP

Everything works fine, except for my (newly installed) Ubuntu 6.06 Server connected to the LAN, and configured to get a dynamic ip from IPCOP. Ubuntu gets an IP.

However, as soon the Ubuntu Server is running, none of the computers on the LAN can't resolve names (DNS) anymore. A tracert then only shows IP-adresses, no names. Browsing (and anything else) only with IP-adresses continues to work

I found out that this seems to be related to the SMC. When I restart the SMC after Ubuntu bootup, everything is back to order until ....... next time I bootup Ubuntu.

I tried already to disable IPV6 based upon the idea the SMC might have problems with that, but no luck

Anyone with bright ideas why the Ubuntu bootup messes up the SMC ? 
Could this be DDNS related ? 
Is this per default active in Ubuntu ? 
How can I disable this per command-line (Ubuntu-server) ?

......

Thanks in advance

---

### Post by tbonius on 2006-09-19
Too vague.  You are getting IP connectivity but no DNS resolution?  What DNS nameservers do your clients have configured?  What is DHCPD handing out for DNS addresses?

T

---

### Post by wquatan on 2006-09-19
> **tbonius said:**
> Too vague.  You are getting IP connectivity but no DNS resolution?  What DNS nameservers do your clients have configured?  What is DHCPD handing out for DNS addresses?

T

All computers use the DNS from IPCOP, IPCOP the DNS from SMC, SMC the DNS from provider.
I repeat, everything works fine (since years) als long I don't connect the Ubuntu to the LAN, as I explained in my original post

---

### Post by tbonius on 2006-09-19
This sounds kind of j00kie.  I have never personally used IPcop so I am not sure.. but why not just use IPtables since it comes the Linux kernel anyways?  You can also configure a local DNS and DHCP server and then pass out the IP settings directly with DHCP and have your clients use your IPtables firewall as their default gateway, DNS, and DHCP server directly?  If you need help setting this up.. let me know.

T

---

### Post by wquatan on 2006-09-19
> **tbonius said:**
> You can also configure a local DNS and DHCP server and then pass out the IP settings directly with DHCP and have your clients use your IPtables firewall as their default gateway, DNS, and DHCP server directly?  If you need help setting this up.. let me know.

T

That's exactly what IPCOP does for my LAN-computers
I know the setup isn't conventional and that I don't need two firewalls, DNS-servers and DHCP-servers.

But still there is IMHO no reason why Ubuntu "messes-up" the DNS in the SMC-router. The Ubuntu gets (like all other computers on the LAN) all information needed from IPCOP together with the IP-address, no difference

Something is conflicting with or confusing the SMC......, and only during the bootup, as after a reset of the SMC-router everything works fine again, for all computers, including Ubuntu

---

### Post by FredSambo on 2006-09-19
what nameservers are in your /etc/resolv.conf file?

try adding a few generic ones, like:

```
search server
nameserver 145.253.2.75
nameserver 193.174.32.18
nameserver 194.25.0.60
```

...and then do sudo /etc/init.d/networking restart

---

