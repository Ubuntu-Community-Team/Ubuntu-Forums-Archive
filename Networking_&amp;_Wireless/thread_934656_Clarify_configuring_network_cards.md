---
title: "Clarify configuring network cards?"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by nbakewell on 2008-09-30
I'm doing a networking project and I've come across a portion that has to do with making two virtual machines talk to each other by configuring the network card.  However, I am new to Linux and networking in general, and I was hoping someone could clarify to me what exactly I'm supposed to be doing - I'm not asking for you to tell me how to do it, I just am having a hard time understanding what *it* is.  Anyways, any help would be much appreciated.  

> Configure the computers to use the network card that connects them to the other Linux computer. Assign the IP address statically. You will be working in an environment with three physical subnets: one connecting the Redhat Server and its Ubuntu client, one connecting the Redhat Linux subnet to the Windows subnet, and one connecting the Windows Server to its Ubuntu client.  You will use 192.168.10.0 for the Redhat subnet.  Use 110 for the host part of the IP number on your "edge" computer, and 120 for the host part of the IP number on your gateway computer. Your two computers should be able to communicate with each other.  These basic "network services" should start automatically each time your computer boots up.

---

### Post by lisati on 2008-10-25
> **nbakewell said:**
> I'm doing a networking project and I've come across a portion that has to do with making two virtual machines talk to each other by configuring the network card.  However, I am new to Linux and networking in general, and I was hoping someone could clarify to me what exactly I'm supposed to be doing - I'm not asking for you to tell me how to do it, I just am having a hard time understanding what *it* is.  Anyways, any help would be much appreciated.

This answer might be considered as a "bump" on behalf of the OP.

First question: are the "virtual machines" on the same computer or on different computers? (If they're on the same physical computer, I suspect that there might be a better way than going through the network card, but have no idea how to do it)

---

