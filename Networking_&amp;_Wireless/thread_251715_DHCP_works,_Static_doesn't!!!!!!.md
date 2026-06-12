---
title: "DHCP works, Static doesn't!!!!!!"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by whatalotta on 2006-09-05
I can connect to the internet no problem using a DHCP configuration.  Problem is that I want to assign a Static IP address to this box.

From reading the troubleshooting guide and a whole lot of posts this afternoon, I can give the following info:

1) Driver appears to be 8139too
2) Modprobe works
3) Get output with ifconfig for eth0 (which I think means that the driver works fine)
4) Can ping localhost (127.0.0.1)
5) Can't ping eth0 (192.168.0.101)
6) When I set up the interfaces file to DHCP, everything works.

I can't figure out why I can't setup this box for static IP.  I have been able to do it on any other distro.

Can someone help?

Thanks!

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-05
A Static config should work fine insofar as the subnet mask and the default gateway/address are properly configured. 

What are your current settings? ((i.e What iP are you assigning your box? What is your router's LAN IP? ))

~b-Dub!

---

### Post by whatalotta on 2006-09-05
First, thanks for the reply.

After seeing your reply, I went back to the static configuration and restarted networking.  This time, I used network-admin, and all worked.

Not sure what happened.  The only thing I can think of is that I put a comma in someplace instead of a period.

:redface:

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-05
Excellent! :p

---

