---
title: "DHCP does not work since upgrade to 8.10"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by venk on 2008-11-16
Hello, 

Just upgraded my computer to 8.10 to see if another problem "firefox frequent hanging with dark screen" will go away  and i noticed that when the computer came back up it would not connect to network.

After struggling for a while i changed the IP to static  and it works fine.

This is the case in both wired and wireless network.

Since this was working fine under 8.04 about 2 hours ago, I am guessing this is a 8.10  issue.

For now, i am ok using static.  

However, any help for a permanent solution would be great.

Thanks.
Venk.

---

### Post by xen-uno on 2008-11-16
Does the static address survive reboot? See here ...

[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

... which will be permanent. I used the 2nd method. The base (internet) connected NIC is ultra reliable (DHCP) here. I had to use the above for the 2nd, LAN connected NIC (trying to get DHCP server working on it for ICS ... no luck so far).

---

### Post by venk on 2008-11-16
Yes static IP survives.  

I used the graphic solution proposed.  

It bothers me that dhcp stopped working with 8.10  This will be a problem when i take the computer to a cafe etc.

I would like to get DHCP working again or going back to 8.04.  How do i do that?

---

### Post by Altmerman on 2008-11-16
I have the same problem. DHCP doesnt work. No, it works partially - I get ip adress,dns, but cannot connect to internet. WinXP network works allright, so I think it's 8.10 problem. Can anybody tell how to fix this?

---

