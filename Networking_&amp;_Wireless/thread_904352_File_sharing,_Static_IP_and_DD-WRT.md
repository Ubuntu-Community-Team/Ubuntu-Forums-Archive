---
title: "File sharing, Static IP and DD-WRT"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by waynemeister on 2008-08-29
Hi all.

Firstly I'd like to say this place has been a terrific resource for my ubuntu adventure so far!

I've recently set up an ubuntu desktop as a file server (CLI too daunting for me just now!) anyways since it is a server it would require to have a static IP. Now I know how to set a static IP within ubuntu but how do I set my router so that even the computer with the static IP will still be able to access the internet? My router is WRT54G with the latest DD-WRT firmware. 

Thanks!

---

### Post by jigsaws on 2008-08-29
You should buy static IP from your provider or use dynamic dns (i.e. dyndns.org or no-ip.com). Then you have to forward ports on your router. 

But I'm not sure it's good idea to open access to fileserver from the Internet (if it is nfs or samba, ftp and scp should be ok).

---

### Post by ilrudie on 2008-08-29
In dd-wrt you can also put a computer in the dmz (e.g. no firewalls just NAT masquerading)

---

