---
title: "Orinoco Gold"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by omenix on 2006-07-29
Hi guys,

I have problem with my orinoco card on ubuntu 6.06 dapper TLS, when I inserted the card it detected as two cards which is wifi0 and eth2 my ipw2100 card is working just fine but my orinoco is not .. here's are some logs:

Jul 29 18:12:59 localhost kernel: [4295492.238000] ADDRCONF(NETDEV_UP): wifi0: link is not ready
Jul 29 18:13:25 localhost kernel: [4295518.045000] ADDRCONF(NETDEV_UP): eth2: link is not ready

---

### Post by omenix on 2006-07-29
Oh btw, Im using Acer Travelmate 290 laptop.. my orinoco card are working normally on compaq laptop..

---

### Post by tturrisi on 2006-07-29
What model orinoco gold?
There are many incarnations of that card, using different chipsets: prism, hermes1, hermes2, lucent-agere, atheros.

I have 2 orinocos: a lucent chipset which uses the orinoco_cs drivers & an atheros chispet which uses the madwifi driverfs, both work out of the box.

---

### Post by omenix on 2006-07-29
Hey you're right.. my chipset is using the lucent-agere ... but at this momment looks like the the kernel module using the hostap driver.. how do I change it? Thanks for your kind help

---

### Post by omenix on 2006-07-29
Btw I just installed the latest orinoco driver.. and is there anything wrong here? 

lsmod |grep orinoco
orinoco_cs             17800  0
orinoco                42900  1 orinoco_cs
hermes                  7424  2 orinoco_cs,orinoco
pcmcia                 40508  2 orinoco_cs,hostap_cs

---

### Post by omenix on 2006-07-29
Hello,

I just found out the solution..

After installing the latest orinoco driver you have to remove the hostap_cs module by running:

rmmod -f hostap_cs
rmmod -f hostap

But how do I remove the hostap modules from loading on boot?

---

### Post by tturrisi on 2006-07-29
you may have to blacklist the hostap driver.

---

