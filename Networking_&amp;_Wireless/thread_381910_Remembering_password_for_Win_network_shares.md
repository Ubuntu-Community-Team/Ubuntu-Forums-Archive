---
title: "Remembering password for Win network shares?"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by LadyFox on 2007-03-11
Hi all, 

Is there a way to get Ubuntu to remember my credentials when i log onto my network shares? I cant seem to fathom it out?

I have just set up my Ubuntu machine, and i have x2 Macs and multiple Windoze machines, all connected to a Win2k3 Server domain. 

(I *think* i have joined the Ubuntu box to the network (any tips for checking, im still a bit of a noob  I can browse my clients under Network Servers, and under Shared Folders ->General Properties my domain name is what it should be? )

I digress, i have no problem accessing my shares (with smb://server/share) but i'd like to not have to enter my credentials each time.  Is there a way around this at all?

Thanks!

---

### Post by dmizer on 2007-03-12
create a mount for your network share in fstab.  the second link in my sig.

using cifs/fstab has a vast number of advantages over using nautilus, not the least of which is the ability to transfer files larger than 2gb.

---

### Post by LadyFox on 2007-03-14
Thanks for that! Shares all mounted and working perfectly! 

Didnt work to start off with, but i replaced //server/share with IP address/share and now its perfect. Shares sat on my desktop, no need to add credentials each time! 

Thanks again!

---

