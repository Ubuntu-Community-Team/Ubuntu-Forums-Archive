---
title: "IP Address filtering"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by exelan on 2008-09-29
Hey there, I have Ubuntu Server running DHCP and DNS for my network.  I was wondering if there was a way to configure it so that only my devices have IP's assigned to them.  
I have DNS configured so hostnames are assigned to each device and associated with their IP's but I would like to make it so that when people come over with laptops when I'm not here, they can't get an IP from my server.

Thanks!

---

### Post by superprash2003 on 2008-09-29
well simple way is to set the exact dhcp range.. for example if you have 5 pcs then set dhcp range such that your router can give only 5 ips.. i.e. say 192.168.1.2 to 192.168.1.6 .. or just disable DHCP in your router and assign static ips to all machines..

---

### Post by Iowan on 2008-09-29
If you wnat to experiment with DHCP, you could set up static leases (based on MAC addresses.

---

### Post by exelan on 2008-09-30
> **superprash2003 said:**
> well simple way is to set the exact dhcp range.. for example if you have 5 pcs then set dhcp range such that your router can give only 5 ips.. i.e. say 192.168.1.2 to 192.168.1.6 .. or just disable DHCP in your router and assign static ips to all machines..

Hey!  Thanks for the quick response!  Yeah, I was thinking that would probably be the best way to do that.  I really appreciate the help!!

---

### Post by exelan on 2008-09-30
> **Iowan said:**
> If you wnat to experiment with DHCP, you could set up static leases (based on MAC addresses.

Oh.... is there a place to define MAC addresses within the dhcp3 server conf file?  Or perhaps a thread that you know of?  Thank you *very* much for your response!

---

### Post by Iowan on 2008-09-30
I haven't tried it yet, but **/etc/dhcp3/dhcpd.conf** has some examples using hardware addresses (certainly look like MAC addresses). Although the example uses a domain name, the documentation mentions using addresses outside the dynamic range.

---

