---
title: "ps3 dissconecting from mediatomb"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by underdog512 on 2008-01-12
I am runing the mediatomb upnp server on ubuntu 7.10 to stream media to my ps3.  my ps3 keeps dissconecting from mediatomb for no apparent reason. I am using a wired connection instead of wireless on my ps3.  

also when I was running mediatomb on fiesty I had this problem sometimes but a restart of my server and my ps3 fixed it every time, but that doesn't seem to be working now that I am running gutsy.  

Any ideas as to whats going on.

---

### Post by underdog512 on 2008-01-16
does anybody out there know anything about this?

---

### Post by Brimick on 2008-01-16
I was having the same problem when I was trying to set up Mediatomb to work with my PS3  earlier today as well. I kept having frequent disconnects, so I downloaded Firestarter. I checked the logs and found the default Mediatomb port (which is something like 49152) and the SSDP port (1900) were being rejected by the computer.

So, I just made a few rules to allow for those ports to be accessible by everyone in the network, and I stopped getting those "PS3 disconnected from media server." messages. Hope this helped a bit.

As for "DLNA protocol error (2103) has occurred"...I'm still tearing my hair out trying to get that from showing up once every 2 seconds. :mad:

---

