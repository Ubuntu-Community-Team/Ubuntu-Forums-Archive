---
title: "Gateway ping problem"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by sunilsivan on 2006-10-10
Gateway ip not pinging 


i am having a pc of AMD 3000+ and installed both win xp and ubuntu 6.06. I am unable to ping my gateway address of my router 192.168.1.1. I am configured my lan card static ip as
ip address - 192.168.1.55
gateway - 192.168.1.1. 
Gateway is pinging on win xp os.
Self ping is possible on ubuntu, but not pinging the gateway ip.
My lan card also enabled.  I am a new commer on linux os. please help

---

### Post by gosh on 2006-10-10
> **sunilsivan said:**
> Gateway ip not pinging 


i am having a pc of AMD 3000+ and installed both win xp and ubuntu 6.06. I am unable to ping my gateway address of my router 192.168.1.1. I am configured my lan card static ip as
ip address - 192.168.1.55
gateway - 192.168.1.1. 
Gateway is pinging on win xp os.
Self ping is possible on ubuntu, but not pinging the gateway ip.
My lan card also enabled.  I am a new commer on linux os. please help


What is in your /etc/network/interfaces ?

---

### Post by mips on 2006-10-10
Please post output of **lspci -v**

---

### Post by Rhaurison Bergamin on 2006-10-10
let us know this output: tcpdump -i eth0 -p icmp -v
When you are trying to ping....

and arp -a too.
ohh, i was forgetting, iptables -nvL

---

