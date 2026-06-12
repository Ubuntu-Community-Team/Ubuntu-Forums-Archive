---
title: "dhcpd"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Gauvenator on 2008-05-26
When I start dhcpd I get a messag about eth0 not being configured and needing a subnet declaration, and also that it is not configured to listen to any interfaces.

How can I make subnet declaration for eth0 in my /etc/dhcpd.conf?

---

### Post by mattress on 2008-05-26
Do you need to have DHCP running on that interface ? Generally you would add  a subnet declaration with the IP address range and options you want handed out to machines on that network range...

Check the man page, there are quite a few good examples there.

-m

---

### Post by slavnist on 2008-05-26
> **Gauvenator said:**
> When I start dhcpd I get a messag about eth0 not being configured and needing a subnet declaration, and also that it is not configured to listen to any interfaces.

How can I make subnet declaration for eth0 in my /etc/dhcpd.conf?

Without knowing which version of ubuntu you are using, the following includes an example of a dhcpd.conf file including the subnet declaration.

[https://help.ubuntu.com/7.10/server/C/dhcp.html](https://help.ubuntu.com/7.10/server/C/dhcp.html)

:)

---

### Post by Gauvenator on 2008-05-26
Wait, to make this machine a dhcp server, do I need it to be on a static IP?  Currently my router is using dhcp.

Here's my  current /etc/dhcpd.conf, which is set up for network booting of thin clients.
```
ddns-update-style             ad-hoc;

option subnet-mask            255.255.255.0;
option broadcast-address      192.168.1.255;
option routers                192.168.1.1;
option domain-name-servers    192.168.1.100;
option domain-name            "example.org";   
option option-128 code 128 = string;
option option-129 code 129 = text;


get-lease-hostnames           true;

next-server                   192.168.1.100;
option root-path              "192.168.1.100:/opt/ltsp/i386";

subnet 192.168.0.0 netmask 255.255.255.0 {
    range   192.168.0.100   192.168.0.199;
    if substring (option vendor-class-identifier, 0, 9) = "PXEClient" {
        filename "/tftpboot/lts/2.6.16.1-ltsp-1/pxelinux.0";
    }
    else{
        filename "/tftpboot/lts/vmlinuz-2.6.16.1-ltsp-1";
    }
}
```

```
Here's the error:

No subnet declaration for eth0 (192.168.1.100).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **


Not configured to listen on any interfaces!
```

---

### Post by mbarak on 2008-05-26
your subnet declaration gives addresses in the 192.168.0.0 network while your eth0 belongs to the network 192.168.1.0

you SHOULD have your dhcp server on a static IP, but you might be able to run it on a dynamic address. just restrict the addresses that your router gives out, and tell your dhcp server (your computer) to give out the other addresses. also make sure your server is the first computer to be turned on in your network

also, you are going to want to make your server authoritative so that your clients don't get their ips from your router

---

### Post by Gauvenator on 2008-05-26
> **mbarak said:**
> your subnet declaration gives addresses in the 192.168.0.0 network while your eth0 belongs to the network 192.168.1.0

you SHOULD have your dhcp server on a static IP, but you might be able to run it on a dynamic address. just restrict the addresses that your router gives out, and tell your dhcp server (your computer) to give out the other addresses. also make sure your server is the first computer to be turned on in your network

also, you are going to want to make your server authoritative so that your clients don't get their ips from your router

Thank you so much changing the other ips in the config to 192.168.**1**.x worked!

---

### Post by mbarak on 2008-05-26
:) no problem
glad to help

---

