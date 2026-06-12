---
title: "Gutsy: All network working, except 192.168.0..0/24"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by EssBee on 2007-10-22
After a fresh install and also a Feisty -> Gutsy upgrade, I'm having network problems that I think the title describes.

From Feisty and any other OS on this machine, there are no networking problems.

I can access the internet no problem, anything on the local network, 10.0.0.0/24 works fine, ssh/dns/nfs, you name it.

Between my local network (10.0.0.0/24) and the DMZ network (192.168.0.0/24) sits an OpenBSD firewall, which I'm sure there isn't a problem with, unless Gutsy is doing some kind of mild spoofing on packets or something.

I can ping the DMZ (192.168.0.0/24) machines from Gutsy, but when I try to actually do anything, ssh/http/pop3 etc, then nothing gets through, like it's being blocked or there's a routing problem. ethernet is an onboard 3Com 3C920.

Any ideas? I've been playnig with this all weekend trying to figure out and getting nowhere.

---

### Post by staticsage on 2007-10-22
That's a strange problem if it works from all other OSes besides Gutsy.

This may be a little overkill than what you're looking for, but you can try install Wireshark and see exactly what's going on. 

[http://packages.ubuntu.com/gutsy/net/wireshark](http://packages.ubuntu.com/gutsy/net/wireshark)

---

### Post by digitalbenji on 2007-10-22
Hi,
   I'm guessing this problem is because the default route metrics have been changed with Gutsy.  From the Release Notes:
> Route metrics
      ifupdown now sets the default route metric to 100 for interfaces with no metric option set in /etc/network/interfaces. This change makes no difference for most users, but may affect a few users with complex networking requirements. If you rely on the previous default route metric of 0 (zero), edit /etc/network/interfaces and set the metric option explicitly for your interface, for example:
      iface eth0 inet static
              address 192.168.0.2
              network 192.168.0.0
              broadcast 192.168.0.255
              netmask 255.255.255.0
              gateway 192.168.0.1
              metric 0


You can read the release notes here: [Release Notes]("https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes")

Let me know if that helps,
Thanks,

---

### Post by EssBee on 2007-10-22
I'd checked that digitialbenji, but thanks anyway.
Manual with metric 0, or dhcp it's just the same.

What I have just found, is that if I change from 'modulate state' and 'keep state' between my screened LAN (10.0.0.0/16) and my DMZ hosts on 192.168.0.0/8, then all is good.

I may be wrong, but it seems to me that there is some, probably security related, change in networking in Gutsy, maybe in the IP stack, that has clashed with my firewall rules.

I may look into this further if I have time. In the meantime, if I can provide any more feedback on the subject, feel free to ask.

Thanks for the prompt responses.

---

### Post by dgrafix on 2007-10-23
Im trying to set up NFS too, I want to make my whole lan have permission to access it but i dont understand the wildcard bit, Im used to using a wildcard ie 192.168.0.*

There doesnt seem any logic to 0..0/24?!? :confused:

Ubuntu wont let me enter any . / or * so how am i supposed to do it?

---

### Post by EssBee on 2007-10-24
> **dgrafix said:**
> Im trying to set up NFS too, I want to make my whole lan have permission to access it but i dont understand the wildcard bit, Im used to using a wildcard ie 192.168.0.*

There doesnt seem any logic to 0..0/24?!? :confused:

Ubuntu wont let me enter any . / or * so how am i supposed to do it?

CIDR notation for 192.168.0.* would be 192.168.0.0/24

Try that and see if it solves your problem.

Think of the number after the slash as being the number of bits that can't change to allow the connecting IP address. For each 0-255 quad you need to allow 8 bits to allow the full range.

192.168.0.0/24 = 192.168.0.*
192.168.0.0/16 = 192.168.*
192.168.0.0/8 = 192.*

A single address, ie 192.168.0.20 would be represented as 192.168.0.20/32, so none of the 32 bits (4x8bits)  can change.

Hope that helps.

---

