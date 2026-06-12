---
title: "Having some trouble with likewise open"
date: 2015-05-18
forum: Networking &amp; Wireless
---

### Post by mattig89ch on 2015-05-18
Hidy ho all,

I'm trying to use likewise open to join a virtual linux desktop machine to a virtual domain.

Every time I try to use the gui I get an error saying there was a bad packet transmitted.  Regardless of the username, I'm not sure what to make of this.

The domain name is correct, the username and password is correct.  the machine has a static IP, the DNS is pointed to the server, and the machine has internet access.  To top it all off, the server can ping the virtual machine.

I figure I must be doing something wrong, but I can't seem to find anything wrong with my steps.

I just tried to attach a txt file with the error it gave me, but I got an error message saying it was too large.  Would it help if I just posted that error log?  It is quite long, and I don't want to be a complete.

---

### Post by mattig89ch on 2015-05-20
I hope the forum mods don't get mad at me for bumping this, but I'd really like to know how to use pfsense to join my ubuntu to a domain.

Even better, if I could get it to adhere to group policy.

Edit: just and update, this is the error message I'm getting:
"mgubernick@matt-vboxubuntu:~$ sudo domainjoin-cli join PracticeDomain Administrator
[sudo] password for administrator: 
Joining to AD Domain:   PracticeDomain
With Computer DNS Name: matt-vboxubuntu.PracticeDomain

Administrator@PRACTICEDOMAIN's password: 

Error: DNS_ERROR_BAD_PACKET [code 0x0000251e]

A bad packet was received from a DNS server. Potentially the requested address
does not exist."

---

