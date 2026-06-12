---
title: "fstab problem with 2 routers"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-06-13
ok i have a router from my internet company that is #.#.1.# and the other routher is a wireless from walmart that is #.#.2.# both go in to a switch that is also from walmart same brand as the wireless router. ok here is my problem when I'm wired on the #1# router I can not mount the windows share on the wireless #2# unless I unplug the wire and go wireless. same problem going the other way to. how do i fix this?

---

### Post by new_tolinux on 2010-06-13
Probably not, since the ip-ranges are different.

You should be able to set-up/use both routers, but they have to be in the same ip-range: 123.123.123.xxx and the same subnet-mask.
One possible solution:
Assuming the wired router has IP 192.168.0.1 and the wireless router 192.168.0.2.
Setup DHCP on the wired router to grant the adresses 192.168.0.3 t/m 192.168.0.99 and the wireless router to grant the adresses 192.168.0.100 t/m 192.168.0.199
Also setup the default gateway in the DHCP server to the ip-adress of the router which is actually connected to the internet.

If done correct, you should be able to connect to every pc on your network and you should be able to browse the internet from every pc on your network.

---

