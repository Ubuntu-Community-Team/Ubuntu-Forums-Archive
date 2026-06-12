---
title: "Xubuntu, Verizon DSL, netgear router and no connection"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by delphis on 2008-05-12
I'm having trouble getting my linux box to connect to the internet even though windows machines can.

Here's my setup - please ask for more info if needed:

- Verizon DSL which uses PPPoE.

- A westell versalink 327W dsl modem set to bridge mode and no dhcp assignment (so it should be just a modem, not a router).

- A MR814v2 Netgear router is connected to the dsl modem (WAN port of the router to port 1 on the modem).  The router is taking care of logging into my ISP and DHCP since the modem is just a bridge.

- A windows box is connected to one of the ports on the router and my linux machine is connected to another - both wired connections.

- Assigned IP addresses based on MAC addresses for both the windows and linux machines.

- I am running Xubuntu 7.04.  I downloaded the network manager applet (nm-applet) and used it to assign a static IP to the linux machine using the router's ip as the gateway.

I can connect to the router's configuration pages, but I can't connect to the internet.  

Any help would be greatly appreciated.  Thanks.

---

### Post by superprash2003 on 2008-05-13
in the terminal type ping google.com and post output here

---

### Post by delphis on 2008-05-13
$ ping google.com
ping: unknown host google.com

---

### Post by superprash2003 on 2008-05-13
are you able to open [http://64.233.187.99](http://64.233.187.99) .

---

### Post by delphis on 2008-05-14
aha...very interesting...

yes i can open it if i put in the numbers.  i take it that means that the DNS server for machine is not configured correctly...

---

### Post by delphis on 2008-05-14
So feeling optimistic, I tried disabling ipv6 as suggested in [this link]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-1b12c0a8c765a0d0d623e3ee60daf197a5bf2b59-2"), but it didn't work.

Here's the DNS configuration from 'ipconfig /all' from my windows machine:
DNS Suffix search list          verizon.net
DNS servers                     71.243.0.12
                                71.250.0.12

and here's what /etc/resolv.conf looks like on linux:
$ less resolv.conf
nameserver 71.243.0.12
nameserver 71.250.0.12
search verizon.net

in case that's helpful.

---

### Post by superprash2003 on 2008-05-14
it would be better to change your DNS servers to opendns .. try this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by delphis on 2008-05-14
didn't work - i also tried changing my /etc/resolv.conf file to have:

nameserver 208.67.222.222
nameserver 208.67.220.220

as well, but that didn't work.

i would think that if the opendns would work, so would the verizon one (even if, as i saw from the link, it's loads slower).

---

