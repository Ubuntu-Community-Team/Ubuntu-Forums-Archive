---
title: "Wireless card not detected"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by gfant on 2008-01-25
i just got my Ubuntu set up on my laptop but i cant get my wireless to work with it i am printing out the guide on Ubuntu but if you can help me out with anything with setin it up 

i don't have a wired just wireless on my laptop......Ans it say no wireless extension i cant get it to see my wireless card i have the cd for it but it says that "Couldn't' display"/media/SMC2635W/SMSetup

---

### Post by hahahan on 2008-01-25
gfant,

You should not print the guide but READ! it and learn from it.
Rome wasn't also build in one night.

---

### Post by Kevbert on 2008-01-25
Try running the command 
lspci -v | less
in terminal.  From this you may see your wireless device and its chipset.  
You'll need to know what chipset the card is based upon (eg Broadcom, Ralink) so that you can search the forums for the solution.

---

