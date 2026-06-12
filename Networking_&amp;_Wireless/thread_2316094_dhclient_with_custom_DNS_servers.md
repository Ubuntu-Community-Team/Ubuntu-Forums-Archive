---
title: "dhclient with custom DNS servers"
date: 2016-03-04
forum: Networking &amp; Wireless
---

### Post by gc55555 on 2016-03-04
I've set up my own DNS server for my home networks.

I'd like to configure dhclient to setup my home domain and DNS server if I'm connecting to my home network, but use the DNS servers provided by the DHCP server when I'm connecting to any other network. Is that possible, na dhow is it done?

---

### Post by papibe on 2016-03-05
Hi gc55555.

First idea: it is not much difficult to setup a DHCP server, and set it so it sends the local DNS as part of the lease.

This way you don't have to do anything to the client computers. This is what I do BTW: my home server runs DHCP and DNS. The easier way to do this is to use the package 'dnsmasq'. Alternatively, you can setup the combo isc-dhcp-server and bind.

One of the best advantages of this setup is that the DHCP leases are added to the DNS, so you have local name resolution.

If that doesn't work for you:

The simplest way that I can think of would be to add another profile to 'Network Connections'.

The one that already exists should be OK for general DHCP. You can rename it as 'DHCP'.

Name the new one as 'HOME'. Then edit it, and go to the 'IPv4 Settings' tab, and select 'Automatic (DHCP) addresses only', and finally set the DNS of your choosing below.

Both profiles will be available on the drop menu available on the network icon on the top panel. You can switch between them whenever you want. It is not automatic, but you can set one as default ( set on 'Automatically connect to this network when available'), and the least frequent to not to connect automatically.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by SeijiSensei on 2016-03-05
I'm not sure I understand the question.

If you have a functioning local DNS server, it will obtain the address for any machine on the Internet provided it can connect to the root name servers.  I run a local nameserver in my home/office network, and it is my primary server for all purposes.

Here's a little experiment you can try.  On a client workstation, open a terminal and enter the command
```
host ubuntuforums.org ip.of.your.server
```
On the machine I am typing on now I get this result:
```

$ host ubuntuforums.org 192.168.100.100
Using domain server:
Name: 192.168.100.100
Address: 192.168.100.100#53
Aliases: 

ubuntuforums.org has address 91.189.94.12

```

This server also has local information for my domain and PTR records for the 100.168.192.in-addr.arpa reverse domain.  Suppose the server contains the zone file for example.com.  Then if I look up [www.example.com](www.example.com) on a client machine, I'll get the A record from my local server.  If I look up ubuntuforums.org, I'll get the address above.

I also maintain a public server for my domain with different address information than that stored on 192.168.100.100.  For instance, if someone asks for mail.example.com on the Internet she will get a different answer for that query than if I look it up on my local network.  That's because I have a public mail server on the Internet, and a private mail server here in my home.

DNS servers cache results to speed up later queries for the same hostname.

---

