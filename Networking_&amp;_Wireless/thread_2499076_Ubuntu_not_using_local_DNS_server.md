---
title: "Ubuntu not using local DNS server"
date: 2024-07-10
forum: Networking &amp; Wireless
---

### Post by jfaberna on 2024-07-10
I like to setup a local DNS Server and include DNS records for each of my local computers, printers, and servers.  This saves me from remembering IP addresses.

Since I'm use a raspberry pi with pi.hole ad blocker I just use its Local DNS server.  To make this all work I just have to change my AP/router's DHCP Server's DNS entries to have the first entry be my pi.hole device's IP.  This all works as far as ad blocking is concerned, but all my Ubuntu based clients don't use the DNS server.  However, my Debian 12 and Archlinux clients do use the DNS server and the hostnames are all recognized.

On a Kubuntu 24.04 client I'm testing, here is what it sees.  My DNS server is at 192.168.68.30 and kubuntu is one of my media servers. As you can see the kubuntu name is not known.
```
resolvectl status
Global
         Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
  resolv.conf mode: stub

Link 2 (enp3s0)
    Current Scopes: DNS
         Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 192.168.68.30
       DNS Servers: 192.168.68.30 8.8.8.8

Link 3 (wlp1s0)
    Current Scopes: DNS
         Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 192.168.68.30
       DNS Servers: 192.168.68.30 8.8.8.8

jim@jim-nucboxg3:~$ nslookup kubuntu
Server:         127.0.0.53
Address:        127.0.0.53#53

** server can't find kubuntu: SERVFAIL


```

However if I'm on my iotstack client (Debian 12 Raspberry Pi OS) and use the host name of my media server, kubuntu, it finds it.
```
pi@iotstack:~ $ nslookup kubuntu
Server:         192.168.68.30
Address:        192.168.68.30#53

Name:   kubuntu
Address: 192.168.68.67
```

I have even tried adding the Local DNS servers IP to WiFi network settings for IPv4 but that doesn't work. I even did one test with adding it the netplan file for the wifi port.

Any ideas?

---

### Post by &amp;KyT$0P# on 2024-07-10
> **jfaberna said:**
> all my Ubuntu based clients don't use the DNS server.

How are you determining this?

Not being able to look up a no-dot hostname is expected when using systemd-resolved, so that doesn't tell whether your DNS server is being used.

> my Debian 12 and Archlinux clients do use the DNS server and the hostnames are all recognized.

How do you have DNS set up in your Debian 12 and Arch Linux systems?

---

### Post by jfaberna on 2024-07-10
> **halogen2 said:**
> How are you determining this?

Not being able to look up a no-dot hostname is expected when using systemd-resolved, so that doesn't tell whether your DNS server is being used.


How do you have DNS set up in your Debian 12 and Arch Linux systems?

On Debian and Arch (Endeavour OS) systems they are not touched so everything is automatic as far as DNS is concerned.

If a lack of no-dot hostnames is the problem, I can add .home or something to the hostname and test that.

---

### Post by jfaberna on 2024-07-10
We are getting somewhere.  I changed kubuntu dns record to kubuntu.home and now nslookup kubuntu.home is showing:

```
jim@jim-nucboxg3:~$ nslookup kubuntu.home
Server:         127.0.0.53
Address:        127.0.0.53#53

Non-authoritative answer:
Name:   kubuntu.home
Address: 192.168.68.67
```


When I put the following in a browser I get to the local web page I expect.
[http://kubuntu.home:6544/dashboard/status](http://kubuntu.home:6544/dashboard/status)

All of this was tested on  a Kubuntu 24.04 PC on real hardware.  So maybe this is a fix?  Not sure why the nslookup show the server as 127.0.0.53?

On a Debian 12 system I see this:
```
pi@iotstack:~ $ nslookup kubuntu.home
Server:         192.168.68.30
Address:        192.168.68.30#53

Name:   kubuntu.home
Address: 192.168.68.67
```

---

### Post by currentshaft on 2024-07-10
Don't use nslookup for network troubleshooting, it's ancient and mostly useless. Use dig or host commands.

It's likely not working because you need to append a search domain to your client resolver configuration.

---

