---
title: "Linux Network - resolve hostnames to IP addresses?"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by bazzer on 2008-01-03
Hi there
I'm looking to create a list of hostnames and associated IP addresses of the Ubuntu clients on my network. We have a DHCP server that doesn't display the hostnames, just the MAC addresses. I've converted a load of PCs from Windows to Ubuntu and named all the PCs with meaningful names, so that I can identify them geographically (for when I may need to ssh into a particular one for example)

All my searches have revealed so far are things like 'install winbind' or 'use dns'. I admit I don't fully know what I'm doing but it does sound to me like I need WINS to work on the network?
TIA

---

### Post by linuchsan on 2008-01-03
type  smbstatus in the console on the server which runs samba.

---

### Post by Predator[23rd] on 2008-01-03
Hi!

> **bazzer said:**
> All my searches have revealed so far are things like 'install winbind' or 'use dns'. I admit I don't fully know what I'm doing but it does sound to me like I need WINS to work on the network?
TIA

there is no need for such a difficult setup. just edit your */etc/hosts* file, something like:

[I]192.168.1.10  galactica
192.168.1.11  pegasus
192.168.1.12  atlantia
192.168.1.13  columbia
[/I]

this will give you the "ability" to type **ssh atlantia** instead of **ssh 192.168.1.12**. If you need such a funtionality on your other computers copy the hosts file to them. that's it.

---

### Post by bazzer on 2008-01-04
> **'Predator[23rd] said:**
> Hi!



there is no need for such a difficult setup. just edit your */etc/hosts* file, something like:

[I]192.168.1.10  galactica
192.168.1.11  pegasus
192.168.1.12  atlantia
192.168.1.13  columbia
[/I]

this will give you the "ability" to type **ssh atlantia** instead of **ssh 192.168.1.12**. If you need such a funtionality on your other computers copy the hosts file to them. that's it.

Hi - can't see that being much good to be honest. The DHCP server can (and I think does) dish out different IP addresses for the boxes on a pretty irregular basis. If the IPs were all static I'd have no problem! Thanks anyway for trying!

And linuchsan - I've not got Samba installed anywhere on that network. Maybe I'll have a look through the man pages to see if it'll help.

---

### Post by Predator[23rd] on 2008-01-04
> **bazzer said:**
> Hi - can't see that being much good to be honest. The DHCP server can (and I think does) dish out different IP addresses for the boxes on a pretty irregular basis. If the IPs were all static I'd have no problem! Thanks anyway for trying!

The DHCP server can dish out different IPs on request - but does not have to. You can also set it up to assign given IPs to given MAC addresses.

I am running two DHCP servers, one at home for my private two machine network and one at a friend/clients 15 machine business network. On both I have a MAC based ACL with static IPs and only 2-3 extra DHCP slots in case a guest computer (business associate) shows up and needs internet access. That way the network is much safer.

Anyway, I am not aware of any build in functions to keep track of DHCP clients based on their computernames while they have truely dynamic IPs. However, it should be possible to write a simple script which updates the *hosts* periodically...

---

