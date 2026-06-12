---
title: "Lost my wireless card on upgrade"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by s_x_g_t on 2009-10-11
My wireless card worked perfect with Ubuntu 6 and I didnt have to do anything, it just worked from the get go!   today I burned an Ubuntu 8  ISO CD and upgraded my computer from 6 to 8. Now my wireless card is not working. Not sure what to do. Its a Blitz brand card. :confused:

---

### Post by anewguy on 2009-10-11
One would suspect you lost your wireless driver in the upgrade, particularly if you did a new install using the CD.

Go to a terminal window (Applications/Accessories/Terminal) and type:

lspci <press enter>

Copy the output and paste it in a reply here.  From that we should be able to determine the chipset and hopefully find you the driver you need to get your wireless going again.

BTW - do you have the Windows drivers for the adapter?

Dave :)

---

### Post by s_x_g_t on 2009-10-11
00.09.0 Network COntroller: ADMtek ADM8211 802.11b wireless interface (rev11)

---

### Post by s_x_g_t on 2009-10-11
ahh well.  Its working now on Ubuntu 


but the driver is not working on my Windows XP, I dual boot you see.

---

### Post by s_x_g_t on 2009-10-11
the antenna is so messed up. I'm thinking about just going to walk mart and getting a whole new card.

---

