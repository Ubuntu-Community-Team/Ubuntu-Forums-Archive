---
title: "Multiple ISPs"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by issya on 2007-04-05
Does anyone know of a way to have a network use multiple ISPs and switch from one to another automatically if one goes down? Right now at my small office we have roadrunner going into a router and then the network. I am going to be getting Verizon DSL as a backup ISP. If Roadrunner went down is there a way for me to auto switch everyone to the Verizon?

---

### Post by mssever on 2007-04-05
> **issya said:**
> Does anyone know of a way to have a network use multiple ISPs and switch from one to another automatically if one goes down? Right now at my small office we have roadrunner going into a router and then the network. I am going to be getting Verizon DSL as a backup ISP. If Roadrunner went down is there a way for me to auto switch everyone to the Verizon?

I don't have a complete solution, but here are some thoughts. You probably need a Linux machine with three (at least) netcards. Standard router boxes don't generally offer enough configurability; so you'll have to set up your own router (probably with NAT). Basically, you'll probably need two upstream connections and a method to test them (perhaps a cron job). Then you route downstream connections to one or the other netcard based on which one is up. This is quite possible, but since I've never done anything remotely similar, I'm afraid I can't be more specific. At any rate, it'll probably become quite technical to configure.

---

