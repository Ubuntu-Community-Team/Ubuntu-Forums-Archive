---
title: "change in wired Ethernet card"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by chettyk on 2007-01-05
I run a SAMBA server using a Dapper Drake server installation. The wired Ethernet port (eth0) is built into the Intel motherboard. As the built-in Ethernet port developed a fault, I have installed an additional wired Ethernet card (eth1). When I boot the SAMBA server, it continues to use the eth0 port. I don't have any desktop installed. Which configuration files do I have to edit and what changes do I need to make in those configuration files so that the SAMBA server uses the eth1 port?

Thanks.

---

### Post by scrooge_74 on 2007-01-05
check your smb.conf file it may be pointing to eth0 as your ethernet card

There is an option to bind the samba server to a specific card

/etc/samba/smb.conf

---

### Post by chettyk on 2007-01-05
> **scrooge_74 said:**
> check your smb.conf file it may be pointing to eth0 as your ethernet card

There is an option to bind the samba server to a specific card

/etc/samba/smb.conf

scrooge_74 thanks for the suggestion. I think, however, the problem is more than just changing the smf.conf file. I am not able to use 'apt-get update' and 'apt-get upgrade' either. There must be a way of making eth1, rather than eth0, the default wired port.

---

### Post by scrooge_74 on 2007-01-05
OK, look in /etc/network/interfaces and see if your new card is listed and then comment out eth0 which is the old card.

But first 
 in the Bios you should desable the old card so to avoid conflicts, that way probably the new card can be recognize as eth0

---

### Post by chettyk on 2007-01-05
After some Googling, I figured out the answer. I had to edit the **/etc/network/interfaces** file.

Original /etc/network/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

I simply changed "eth0" to "eth1" in the two lines for the primary network interface. Voila!

---

### Post by chettyk on 2007-01-05
> **scrooge_74 said:**
> OK, look in /etc/network/interfaces and see if your new card is listed and then comment out eth0 which is the old card.

But first 
 in the Bios you should desable the old card so to avoid conflicts, that way probably the new card can be recognize as eth0

Thanks, scrooge_74 for the tip. But even before that, I found out the answer by Googling. Simply changing "eth0" to "eth1" in the  /etc/network/interfaces file did the trick. So far, I have had no conflicts and the system seems to be working smoothly. 

It hadn't crossed my mind that one could disable the built-in network interface card through the BIOS. Must check if the option exists. Even if it did, I don't think I'd use it now that I have the SAMBA server up and running again.

Many thanks, scrooge_74

---

### Post by chettyk on 2007-01-05
> **scrooge_74 said:**
> 
But first 
 in the Bios you should desable the old card so to avoid conflicts, that way probably the new card can be recognize as eth0

I couldn't find any way to disable the old card in the BIOS. And as eth0 is built into the motherboard, there is no way to remove it either. Doesn't matter, though, as the fix seems to be working fine. Thanks for the suggestion, scrooge_74.

---

