---
title: "Connecting to Vista[Solved]"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by manatee7 on 2007-10-13
I'm having problems connecting to Vista shares and printers through local network.

I've got the latest samba available via repository, and have tried most of the suggestions i could find on google, less the registry hack (i think it is for going vista -> linux anyway)

I can browse and see the vista machine under windows network > workgroup > user-pc

but when I try and open the vista computer, I'm prompted with a login box for guest@user-pc (guest? I'm guessing a vista thing).

I've tried my vista user / pass and my ubuntu user / pass both to no avail. 

Any ideas?

---

### Post by manatee7 on 2007-10-15
After endless googling, I thought I would try something else.

Since it was only the login that wasn't working (the machine and workgroup could be seen), I decided that perhaps, for some reason, vista required a password in order for my ubuntu box to be able to access it.

Low and behold, setting a password in vista allowed my ubuntu machine to access printer and file sharing, for the other people in this situation, and there is lots of them as per google. 

There's your solution, anyone know why?

---

