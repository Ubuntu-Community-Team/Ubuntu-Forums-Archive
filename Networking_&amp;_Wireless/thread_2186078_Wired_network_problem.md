---
title: "Wired network problem"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by wolfen10862 on 2013-11-05
Hi, I have three wired computers and 5 phones and a couple of tablets all linked through a netgear router, The computer I am on now and one other computer have 13.10 on them fully updated, the other wired computer has windows xp, if I click brows network I can only see the windows computer, why is that, and what do I need to fix it? I'm not too concerned about the phones and tablets, but the computers I would like to be able to see in  my home network, especially since after installing Ubuntu I will NEVER go back to any form of windows.

---

### Post by ian-weisser on 2013-11-05
Is there some reason you want to see them?
Printer host? Shared storage? Service?

Ubuntu systems generally don't broadcast their existence on a Samba (or Avahi or any other) network; they do broadcast the availability of specific services.

Also, please specify which kind of networking you want to use. Samba (Windows) or Avahi (Bonjour) or Netatalk (Apple) or others.
You may be used to Samba (Windows) networking. Unless you want to share services with/from a Windows box, easier alternatives may be available.

---

### Post by wolfen10862 on 2013-11-05
Basically all I want is to be able to print from all three and share files between them, and see them on the network. My youngest son has a large music file that he used to keep on MY computer ion teh shared folder on windows, and I used to download files, pictures, and stuff like that and put it on their computers.

One compute is windows, two are Ubuntu 13.10.

---

