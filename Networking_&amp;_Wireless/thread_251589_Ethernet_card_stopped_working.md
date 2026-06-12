---
title: "Ethernet card stopped working"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by Julolidine on 2006-09-05
Mysteriously, my ethernet card just stopped working.  Last night, I downloaded a distro of Quantian, burned it, then restarted my computer into XP.  I then live booted Quantian, and now when I go back to Ubuntu the ethernet does not work.  ](*,) 

The ethernet card is activated, and my router shows the computer being connected (sees the MAC from the card).  

I've tried limited things, like deactivating, and then reactivating the card.  I searched the forum, but it didn't appear to be a common problem.  

Any advice?

---

### Post by whizbaby on 2006-09-05
Can your router do dhcp? If yes type **sudo dhclient eth0**.
If not, do you have any IP assigned and is it in a subnet of the router's IP?

---

