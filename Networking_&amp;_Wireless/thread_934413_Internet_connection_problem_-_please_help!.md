---
title: "Internet connection problem - please help!"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by nedthened on 2008-09-30
Hello all.

I installed ubuntu from the cd, foolishly thinking that it would leave my windows vista installation alone, but it didn't and it deleted it. So now i am stuck with just ubuntu and none of my files !!!!

Problem:

MY pc conencts to my belkin wireless router, it says that it is connected to the internet, but mozilla firefox and update applications cannot connect to internet/display webpages!!! :confused:

This is really annoying me, so please could you help. I looked at the dns setting which its using for the connection and the info is wrong.How do i change!!

Thanks in advance
NEd

---

### Post by nedthened on 2008-10-01
Please

---

### Post by Iowan on 2008-10-01
Installation *should* have left used partitions alone - unless you told it to reformat and use the entire drive.  What are results of **ifconfig** and the contents of **/etc/network/interfaces**.  It's possible to prioritize your preferred DNS servers by editing /etc/dhcp3/dhclient.conf and change the line ```
#prepend domain-name-servers 127.0.0.1;

``` - uncomment it (remove the # and insert your server addresses.
(Won't bore you with how-to instructions... unless you ask).

---

