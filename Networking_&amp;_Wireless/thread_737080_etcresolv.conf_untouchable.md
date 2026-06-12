---
title: "/etc/resolv.conf untouchable"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by digital00 on 2008-03-27
Is there a way to make DHCP not change /etc/resolv.conf ?

---

### Post by chilinski on 2008-03-27
I think you're now expected to put "hardwired" stuff in /etc/dhcp3/dhclient.conf. For example, if you put your dns servers in there, you don't have to worry about resolv.conf being overwritten.

For example, in mine I have a line that says:

prepend domain-name-servers 66.28.0.45, 66.28.0.61, 129.250.35.250;

There's another command besides "prepend," but I found info on "prepend" first  so I use it and it works fine

---

### Post by Eiríkr on 2008-03-27
Is there any specific reason to lock down the /etc/resolv.conf file?  If there's data in there you need, either make sure the DHCP server you're using includes that (and therefore will assign it and include it in the data your resolv.conf file gets overwritten with), or add it to the dhclient.conf file as chilinski describes.  

Cheers,

Eiríkr

---

### Post by digital00 on 2008-03-27
> **chilinski said:**
> I think you're now expected to put "hardwired" stuff in /etc/dhcp3/dhclient.conf. For example, if you put your dns servers in there, you don't have to worry about resolv.conf being overwritten.

For example, in mine I have a line that says:

prepend domain-name-servers 66.28.0.45, 66.28.0.61, 129.250.35.250;

There's another command besides "prepend," but I found info on "prepend" first  so I use it and it works fine

Thanks...now it works!! :):):)

---

### Post by Eiríkr on 2008-03-27
Good to hear!  :D  If that does it for you for this thread, then please mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

