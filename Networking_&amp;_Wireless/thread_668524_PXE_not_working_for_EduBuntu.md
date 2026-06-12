---
title: "PXE not working for EduBuntu"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by structured.spirits on 2008-01-15
I have limited Linux experience. I'm running a fresh install of Edubuntu 7.10 Gutsy on a Dell PowerEdge 500SC server. I'm trying to use i386 machines to boot using PXE. WHen I try to boot the thinclient, it connects to the Edubuntu DHCP server and gets an IP, then I get the following messages:

PXE T01 - File Not Found
PXE E3B - TFTP Error
PXE MOF

The server has a single ethernet card which connects to the same hub as the thinclient, which is different from the standard install shown in the edubuntu guide. I have a linksys router, ip 192.168.0.1, but dhcp is turned off. The server's ip is 192.168.0.249

My basic understanding is that the card is communicating with the server, but then the PXE linux kernel is not where the server says it is. Here is my much edited dhcp.conf file.

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386/boot";
next-server 192.168.0.249;


filename "pxelinux.0";
}

As the file indicates, pxelinux.0 is located at /opt/ltsp/i386/boot/, which is a different place that what the original config file suggested. The dhcp.conf file is located at /etc/ltsp and there's nothing else in that folder. Whats going wrong here?

---

### Post by yemu on 2008-01-18
i'm using ubuntu gutsy and also have the same problem but only for some thinclients - compaq deskpro pII. but what's strange some of the clients work. also pIII compaqs work ok.
best regards
y

---

### Post by structured.spirits on 2008-01-21
> **yemu said:**
> i'm using ubuntu gutsy and also have the same problem but only for some thinclients - compaq deskpro pII. but what's strange some of the clients work. also pIII compaqs work ok.
best regards
y

I think that the older (compaq p2 for example) use an older .99 version of intel's PXE which isn't compatible with the modern standard somehow. I think my problem has something to do with where the server tells the clients to look for the pxe linux boot image.

---

### Post by yemu on 2008-01-23
yes, that's true, i upgraded bios and now my thinclients work ok!

---

