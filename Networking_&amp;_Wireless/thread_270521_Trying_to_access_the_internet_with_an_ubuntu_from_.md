---
title: "Trying to access the internet with an ubuntu from a Windows XP(I.E. Yet another noob)"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by Da Choice on 2006-10-03
Right, first I'm running Ubuntu 6.06 installed from a live disk earlier today. I can't find anywhere else that solves my problem directly, so I thought I'd ask you nice folks here to help me =)

Right I can see the other computers(Can't access them but I'm told that by using Samba I can do this easily(Must I install this on both the XP computers and my linux or just my linux?)), I've set a static IP adress that is different from everyone else on the network's one, I've set up the DNS server exactly like the other computers with the defualt gateway, but I can't access the internet. Is this simply my lack of Samba, or is there another way to fix this?

I'm downloading and (hopefully!) installing Samba as we speak, and will try to add more if I can. Help would be incredibly nice =)

P.S. Is there any way to run Windows Games fairly easily on the linux install? Thanks for the help guys!

---

### Post by Iowan on 2006-10-03
Samba (or lack thereof) *shouldn't* affect DNS. Samba will only be required on the Linux (Ubuntu) box.  A static address means the DHCP client (probably) isn't messing with resolv.conf settings. Hopefully, the address you picked is in the same subnet as the other machines.  IPV6 sometimes causes problems.

Windows games will require Wine (or something similar).

---

