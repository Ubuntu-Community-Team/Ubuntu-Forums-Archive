---
title: "Local DNS"
date: 2014-03-31
forum: Networking &amp; Wireless
---

### Post by geidorei on 2014-03-31
Hi folks - confused.com here... I've looked and looked for the answer and just getting more confused.

Right then...

Ubuntu server setup, wordpress setup for the intranet, accesable via 192.168.1.101/wordpress and by editing hosts file on main computers - pegasus.chm/wordpress - all working perfectly.

However, this is where I'm lost - want to setup so that 192.168.251.101 has a name assigned to it on the netwrok automatically, without having to edit all the companies computers host files - name to be pegaus.chm

1. Can i do this via the router (crap one from talktalk)
2. setup via a dns server on the server (if so, help).
3. or just buy a domain name and pouint it to our systic ip.

Any help really appreciated.

---

### Post by geidorei on 2014-03-31
Ok doh! Local DNS I mean !

---

### Post by bapoumba on 2014-03-31
Edited your thread title ;)

---

### Post by SeijiSensei on 2014-03-31
Most routers can act as a DNS server.  Look and see whether you can add names to its hosts table, then make sure the router's address is given to network clients during the DHCP exchange.  It's generally a lot easier to reconfigure your router than to set up a local DNS server.  I'm assuming you've assigned the Wordpress machine a static IP address, so it doesn't already appear in the router's hosts table.

If you're using DHCP with an IP "reservation" for the server, then you can ensure that the router get a specific name for your server by editing the file /etc/dhcp/dhclient.conf.  By default the DHCP client uses the contents of /etc/hostname via the get_hostname() operating system call.  However you can enforce a specific hostname during the DHCP negotiation by changing
```
send host-name = gethostname();
```
to
```
send host-name = pegasus
```
You might need to enforce the .chm domain on the router, though you can try using
```
send host-name = pegasus.chm
```
and see if that works.

If you don't have control over the "talktalk" router, I suggest buying [a router with support for dd-wrt]("http://www.newegg.com/Product/ProductList.aspx?Description=dd-wrt&submit=ene") and placing it behind the talktalk device.

---

### Post by geidorei on 2014-03-31
Thanks

---

### Post by geidorei on 2014-03-31
Hi brilliant many thanks - yep router is a bit pants, technicolor - time to upgrade i think.

---

### Post by bapoumba on 2014-03-31
Do I understand your issue is solved ? Please mark the thread as such (under Thread Tools menu), thanks.

---

### Post by geidorei on 2014-04-01
Maybe not yet ---- working in it. A soon as sorted will put a synopsis for others.

---

