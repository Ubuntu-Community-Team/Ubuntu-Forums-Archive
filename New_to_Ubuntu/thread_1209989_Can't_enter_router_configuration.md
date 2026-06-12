---
title: "Can't enter router configuration"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by akamigs on 2009-07-10
I use 'ifconfig' and type in my ip address into firefox and it gives me the standard "Page Load Error" page.

How do I enter the configuration of my router via wireless?

EDIT: my internet and everything else is working fine.

---

### Post by halitech on 2009-07-10
on the bottom of your router there should be a sticker with info, including the IP address of the router. Use that if you want to connect to the router, not your computers ip.

ps. it should start normally with 192.168.x.x

---

### Post by IHeequ5i on 2009-07-10
The IP address of your PC is *not* the same as the address of your router.  In general, home routers use a 192.168.x.y addressing scheme.  If the IP address of your PC is 192.168.1.3 (for example), it's fairly likely that your router's address will be 192.168.1.1 - in other words, take your PC's address, change the last octet to a 1, and try that.

---

### Post by koleoptero on 2009-07-10
Do you type the correct ip address? One possibility is 192.168.2.1 or 192.168.1.1

---

### Post by LewRockwell on 2009-07-10
> **akamigs said:**
> I us 'ifconfig' and type in my ip address into firefox and it gives me the standard "Page Load Error" page.

How do I enter the configuration of my router via wireless?

most routers can be set so that wireless clients cannot access the configuration via the wifi(safety feature)

you should first confirm that your router settings are correct for wireless access to router configuration(this can be most efficiently done via a wired LAN connection)

if you do not have access to the router or the wired LAN then you may find it necessary to contact your systems administrator for access/instructions

otherwise, some web browser interfaces use "http://192.168.1.1"(linksys factory default)

.

---

### Post by akamigs on 2009-07-10
thanks guys it worked.

my next question is how do i find the router's ip address (in this case 192.168.0.1) using the terminal? compared to Window's 'ipconfig'

---

### Post by halitech on 2009-07-11
you could run ifconfig and look at the default gateway, it should be the routers IP address

---

