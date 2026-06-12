---
title: "Netatalk: cannot see resources"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by nico.benaz on 2008-04-08
Hi,
I am not at all an expert with Appletalk....I need to share some samba-folder with 2 os9.1 macs.

I installed netatalk on my ubuntu, but I cannot see my shares from mac. 
I need to type my server-IP to access them.

I just configure this file:



-----------AFPD.CONF----------

"Public share" -uamlist uams_guest.so -loginmesg "Welcome!"





-----------APPLEVOLUMES.DEFAULT-------------------

/home/pubblica          "Pubblic share"





I was expected my macs see that share by default.

Where do I get wrong?

thank you,
nicola

---

### Post by kidders on 2008-04-09
Hi there,

OSX systems use mDNS (aka Bonjour) to advertise AFP shares & other services (eg iTunes/iPhoto libraries, speakers, apple TVs, and so on) to the network. I imagine OS9 works the same way. If I were you, I'd give avahi a shot ... although any mDNS responder should work just fine.

---

