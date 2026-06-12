---
title: "Cannot ping other machines on my Lan using host names only"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by rnim on 2007-12-02
Hi,

I looked for an answer but none of the treads seem to address my specific situation.  Here goes:

Setup:
- My ubuntu (edgy) machine is called 'mars'
- It is on my LAN.  Everythig is wired.
- Single subnet
- Firmware Version: v1.50.5 on Linksys router, model WRT54GS being used as a router.
- Router is running DHCP server.  Its 'domain' field is set to nothing (i.e. field is empty).
- All machines are set to 'Get my IP automatically from the DHCP server, and automatically configure DNS".
- I have one more Linux machine and a windows machine, and a networked attached storage box.
- No Samba/NFS/Pirnt server
- I can ping any host from any other (which has a prompt to issue ping command) using IP addresses.
- I can ping any host from my windows machine using the other hosts' hostnames (w/o any domain extensions).

Problem:
--> I CANNOT ping other hosts - windows/linux/storage box - using hostname alone from my ubuntu machine (mars).  Remember I can ping them using their IP addresses.

I don't want to add entries into /etc/hosts on mars.

How can I ping other hosts on my network using unqualified host names.

I have spent about a day trying to dif information and experimenting, but to no avail...  almost giving up.  This is my last resort... 

Please help.


Cheers,
rnim

---

### Post by Linteg on 2007-12-02
I think [this post](http://www.linuxquestions.org/questions/linux-networking-3/ping-netbios-names-from-linux-samba-271336/) will help you.

---

### Post by rnim on 2007-12-02
This is a splendid post.  Thank you so much!!

I wish the default contents of nsswitch.conf contained 'wins', or the network setup tool allows setting it up...

---

### Post by freemansteve on 2008-04-05
For some reason whenever I set up an Ubuntu box on my home network consisting mostly of Windows XP machines, all of the following are a complete pain:

- installing Samba
- remembering to sort out the right details in the smb.conf file
- then finding you can see Ubuntu folders from XP, but not XP folders from Ubuntu so you fiddle about with winbind and nsswitch.conf
- you realize ping by hostname only works on the XP units
- it takes hours, because there is so much to remember!!

You know, I think that the Linux/Ubuntu developers are actually being paid by Microsoft to make it hard to mix Ubuntu and Windows, so that it just works out of the box. Either that or Windows is just despised by the Linix community, so they pretent it'll go away by err, making it awkward to mix with!

I reckon the best way to make Ubuntu all-pervasive is to make sure it works out of the box on a home Windows LAN. You shouldn't need to download packages like samba, winbind or DNS, or have to alter conf files - why not make it an install-time option to run right away on a home LAN?

Steve

---

### Post by swordphsh on 2008-04-05
I edited that configuration file from that fourm post and installed the winbind package, but I still cannot ping windows host names.

Also, when I go into the Windows Network browser I can only browse the workgroup that my computer is in. 

I can see the other windows computers that are in my workgroup, I just can't ping them.

---

