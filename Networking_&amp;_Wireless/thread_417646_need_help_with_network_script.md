---
title: "need help with network script"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by meomike2000 on 2007-04-21
I am trying to add a scrip to the file /etc/network/interfaces to add static routes.
not sure if this is the correct way.
this is what i have come up with, can somebody plz let me know if this is correct.

I have wrote the script ( routes.sh ) and the i chmod777 routes.sh

this is an example of what i have added to the file /etc/network/interfaces

code:

#eth1
auto eth1
iface eth1 inet static
         address 192.168.x.x
         netmask 255.255.255.0
         broadcast 192.168.x.x
         post-up /etc/network/if-up.d/routes.sh


the question is: is the correct way to use "post-up",
or is there a better way. this does not seem to work for me so well
interface comes up but the routes i added with /etc/network/if-up.d/routes.sh dont show up.

any help would be appriciated
thanks in advance,

mike

---

### Post by spd106 on 2007-04-22
You don't need to reference the script in the interfaces file, just put it in that directory and make sure it's executable (chmod +x). It should now run whenever an interface is brought up.

---

