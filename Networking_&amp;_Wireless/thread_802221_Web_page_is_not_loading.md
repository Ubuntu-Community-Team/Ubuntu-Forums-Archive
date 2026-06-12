---
title: "Web page is not loading"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by shivam.manjunath on 2008-05-21
Hi All.
I am a day baby to linux. I have installed Ubuntu 7.10.
I have configured the machine with a static ip, no firewall, its a direct connection to the internet. I have a DNS server(its a Enterprise network). I am able to ping internal machine connected to the same network. Others are able to browse(all are using fedora6). But i am unable to get any of the webpages loaded onto my machine. I am able to ping all the websites. But when i browse through Firefox it just keeps on wating and after 4-5 minutes "connection to the server reset" error pops up.
If i connect my windows machine to the same port with same configuration i am able to browse or if i connect this linux machine(two separate systems) to other network which uses DHCP i am able to browse.

Please can anyone help me with this.

Thanks and regards
Shivam

---

### Post by superprash2003 on 2008-05-21
so you want all your clients to use your local DNS server for lookups?

---

### Post by shivam.manjunath on 2008-05-21
No, not all clients. Only for one of our customer

---

### Post by superprash2003 on 2008-05-22
here's how you set DNS servers permanently in linux.. [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) in this tutorial opendns servers are used, you can change it to whatever you like

---

### Post by shivam.manjunath on 2008-05-23
I tried all possib..no progress in solving the issue...
resolv.conf is verified
/etc/network/interfaces is also verified
everything is alright as i found in many posts in the forums
I tried changing the IP also..no luck...
[There is no chance of using DHCP...one and only static IP option..]

---

### Post by shivam.manjunath on 2008-05-23
Few hours back i upgraded from 7.10 to 8.04 through live cd.
But still problem is not solved. Is there any issue with OS in supporting STATIC IP?

Thanks and regards,
shivam

---

### Post by inzi2u on 2008-05-23
Hi, I use Ubuntu 8.04, and there doesn't seem to be any problems with hardy's STATIC IP support.. it works fine for me.

---

### Post by shivam.manjunath on 2008-05-24
Please tell me how to disable/remove ipv6 completely in ubuntu8.04.

Thanks and regards
shivam

---

