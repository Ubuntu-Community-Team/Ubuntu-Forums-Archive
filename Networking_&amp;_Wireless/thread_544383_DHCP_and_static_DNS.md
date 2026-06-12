---
title: "DHCP and static DNS"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by Chris Norris on 2007-09-06
Hi all,
I promise I searched the forum before posting but I couldn't find anything describing this issue although I'm sure the solution exists.

My Ubuntu 7.04 box get's an IP address from the company's DHCP server which also supplies a DNS server and gateway. But I want to use my own DNS server as I have a bunch of test PCs on a test domain.

So I though I could add the DNS nameserver either in resolv.conf or through the GUI using the network admin tool. This works for a while then the DNS server is reset back to the DHCP supplied server causing DNS failures.

How can I have DHCP and static DNS servers? (modding the DHCP server config is not possible)

thanks

Chris

---

### Post by noob12 on 2007-09-06
Edit **/etc/dhcp3/dhclient.conf**

Add or replace a line
```

prepend domain-name-servers *your.name.server.ipaddr*;

```

where *your.name.server.ipaddr* is replaced by your desired name server.  You can list multiple servers in sequence by using a comma-separated list. Don't forget the semi-colon at the end of the line. 

This tells dhclient to prepend these servers to whatever list it gets from the DHCP service when writing the **/etc/resolv.conf**.  You'll see them (listed before the others) in the /etc/resolv.conf after DHCP completes.  Normal resolution semantics then apply to this list, namely  these servers will be used first; if they fail to respond, the client will proceed to following ones, but subsequent servers are not used if any returns an actual result, even if it is NXDOMAIN (i.e. not found).

You can entirely supersede the servers provided by the DHCP service using
```

supersede domain-name-servers *your.name.server.ipaddr*;

```

---

### Post by Chris Norris on 2007-09-06
Thank you, that worked :KS

Chris

---

