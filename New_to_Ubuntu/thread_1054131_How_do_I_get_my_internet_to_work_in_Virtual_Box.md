---
title: "How do I get my internet to work in Virtual Box?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by gymophett on 2009-01-29
I have Windows XP installed on VirtualBox. My internet won't work. It says my ethernet driver is installed. Networking is enabled in the settings on VirtualBox. Nothing works! What do I do? I need it! :(
Thanks for you guys help :)

---

### Post by XanTrax on 2009-01-29
> **gymophett said:**
> I have Windows XP installed on VirtualBox. My internet won't work. It says my ethernet driver is installed. Networking is enabled in the settings on VirtualBox. Nothing works! What do I do? I need it! :(
Thanks for you guys help :)

By default, VirtualBox sets up a NAT environment for easy communication between the host and the guest.

But, since you're messing with Windows...lets do some windows troubleshooting real quick.

Click Start -> click Run -> type "cmd" without the quotes -> at command line type "ipconfig" without the quotes -> post the output here.

---

### Post by gymophett on 2009-01-29
> **XanTrax said:**
> By default, VirtualBox sets up a NAT environment for easy communication between the host and the guest.

But, since you're messing with Windows...lets do some windows troubleshooting real quick.

Click Start -> click Run -> type "cmd" without the quotes -> at command line type "ipconfig" without the quotes -> post the output here.

Heres what is came out with.

Windows IP Configuration

Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix .:
Autoconfiguration IP Adress. . . : 169.254.2.143
Subnet Mask . . . . . . . . . . . : 225.225.0.0
Default Gateway . . . . . . . . . :

---

### Post by XanTrax on 2009-01-29
> **gymophett said:**
> Heres what is came out with.

Windows IP Configuration

Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix .:
Autoconfiguration IP Adress. . . : 169.254.2.143
Subnet Mask . . . . . . . . . . . : 225.225.0.0
Default Gateway . . . . . . . . . :

Interesting.

Can you please go to VirtualBox, click your Virtual Machine, on the right click Network and tell me what it reads for

Adapter Type

and

Attached to

---

### Post by gymophett on 2009-01-29
> **XanTrax said:**
> Interesting.

Can you please go to VirtualBox, click your Virtual Machine, on the right click Network and tell me what it reads for

Adapter Type

and

Attached to

I fixed it! It was set to Not Attached and I changed it to NAT and now it runs smoothly. Thanks anyway. :)

---

### Post by XanTrax on 2009-01-29
> **gymophett said:**
> I fixed it! It was set to Not Attached and I changed it to NAT and now it runs smoothly. Thanks anyway. :)

Welcome :)

---

