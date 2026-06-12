---
title: "Sometimes can't see other computers"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by Drate on 2006-11-24
Ok, I am running Ubuntu Edgy Eft on a small home LAN.  Sometimes when I goto places-> network servers I see other computers on the network.  30 seconds later, I do not.  5 minutes later, maybe I do, maybe I don't.  Why I ask... Why?  I have never seen anything under "Windows Network" etc... only at the first place.  The other computes are all XP machines and see each other fine.  The workgroup name is WORKGROUP and I have indicated such in the Shared Folders dealie.  So yeah... what must I do?

---

### Post by x64Jimbo on 2006-11-24
Aside from writing a letter to MS telling them that they need to fully disclose all their network protocols, I'm not sure what else you can do. All the stuff that we can do that interfaces with Windows is because of some very dedicated individuals who reverse-engineered them. Reverse engineering can produce some great results, but sometimes it's necessary to know more about the inside workings of these protocols, and while SAMBA is a great tool, it hasn't had the benefit of being designed around documented protocol because MS hasn't released any documentation on their SMB protocol. Because of this, SAMBA will sometimes be buggy, and there's not a lot we can do about it.

---

### Post by Drate on 2006-11-25
Oh.

---

### Post by x64Jimbo on 2006-11-25
That said, you may want to look at your network interfaces to make sure they're properly configured. I suspect that if you can see the computers sometimes but not all the time, you're looking at a SMB problem, but it could be simpler than that. Have you checked to make sure that windows file sharing is turned on (and unfirewalled) in all the computers?

---

