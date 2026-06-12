---
title: "cant ping domain names"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by kfridge on 2007-09-14
Hi,

Just installed Ubuntu Server 7 as a LAMP server and its connected to the orange interface (DMZ) of my smoothwall.

I'm a n00b to all this and I don't seem to be able to get DNS to work properly on the server. If I ping a website (e.g. bbc.co.uk) I get an error that it is an unknown host. However, if I ping the domains IP address I get a reply!

So...what on earth is going on!? :confused: 

My resolv.conf is:
nameserver 194.168.4.100
nameserver 194.168.8.100

My network/interfaces is:
auto eth0
iface eth0 inet static
            address 10.0.1.10
            netmask 255.255.255.0
            network 10.0.1.0
            broadcast 10.0.1.255
            gateway 10.0.1.1

what else do I need to check etc. to get this thing working? Eventually I want to get webmin installed and maybe get an FTP server working. I did have all this working on a M$ box but wanted to start using Linux - A bit of a baptism of fire I think!

---

### Post by spd106 on 2007-09-14
Can you ping the nameservers?

---

### Post by kfridge on 2007-09-14
yes...
 
a couple of examples:
I can't ping [www.bbc.co.uk](www.bbc.co.uk)
I *can* ping 212.58.227.77 (which is what [www.bbc.co.uk](www.bbc.co.uk) resolves to on my windows box)

I can't ping krhome.com
I *can* ping 74.52.107.114 (which is what krhome.com resolves to on my windows box)

---

