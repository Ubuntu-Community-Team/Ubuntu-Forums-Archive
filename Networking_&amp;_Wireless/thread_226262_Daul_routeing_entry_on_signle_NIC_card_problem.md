---
title: "Daul routeing entry on signle NIC card problem"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by slo on 2006-07-31
I have ubuntu box, ip : 192.168.1.200/24
and I have two gateway on my network,
one is 192.168.1.1 , the gateway connect to company internal network.
the other is 192.168.1.244, the gateway connect to Internet acceess.
my plan is:
setting 192.168.1.244 as default gateway, then ubuntu can access internet 0.0.0.0/0, and setting a secondly routeing entry 192.168.0.0/8 for access internet network area 

my configuration is :
/etc/network/interfaces 
setting default gateway:192.168.1.244

and use route add command add a secondly routing entry
#route add -net 192.168.0.0/8 gw 192.168.1.1

my question is: I need manual add this secondly routing entry after ubuntu reboot evey time, how can I save this configuration on some config files? Pls don not tell me add to /etc/init.d/local file.
As I know, it is possibly on Gentoo linux with iproute2 module.
So, how can I to do for this on Ubuntu?:confused:

---

### Post by mips on 2006-07-31
add to interfaces file or as a startup script (init.d ???)

---

### Post by slo on 2006-07-31
> **mips said:**
> add to interfaces file or as a startup script (init.d ???)

Could you please post a sample ?
I can not understand how to config this from you messenge.

---

### Post by mips on 2006-07-31
Try adding route add -net 192.168.0.0/8 gw 192.168.1.1 to the bottom of your /etc/network/interfaces file.

Will have to check on the init script.

---

### Post by slo on 2006-07-31
man interfaces will provide andy help for me ?

---

### Post by mips on 2006-08-02
slo,

Did you come right ?

If not please post the following and I'll tell you what to do:

1. Please post output of **ifconfig eth**
2. Please post output of **route -n**
3. Please post output of **cat /etc/network/interfaces**

---

