---
title: "Need help with router connection!"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by ninjip on 2008-09-08
Well I need some driver installation for my wireless internet card. 
Yeah now I'm sure of it I just installed a different assistant for finding networks and it clearly states that it cant find no wireless card. I will need a driver installation to get this working.

as stated below I have a sony vaio model VGN-NR120E.


Edit again: what the heck? after some more looking I found in the hardware drivers some driver called support for atheros 802.11 wirless LAN cards. Now if I'm correct this is supposed to enable proper working of my wireless card? anyhow how can I get my wireless card driver altogether installed on ubuntu? (using wired internet is a pain!)

---

### Post by ninjip on 2008-09-08
edit: nevermind

---

### Post by ninjip on 2008-09-08
Please I need help!

---

### Post by Blackcabs on 2008-09-08
> **ninjip said:**
> Please I need help!

Hi Ninjip can you open a terminal window and type lshw -C network
This will tell us what type of card is in your machine so we can try to solve your problem

---

### Post by timcredible on 2008-09-08
if you have the Windows driver for the card, then install ndiswrapper via synaptic, and then run System->Administration->Windows Wireless Drivers, and point to the wireless driver, then reboot.

---

### Post by ninjip on 2008-09-08
no good. it doesn't find the card. like if it didn't exist =/

---

### Post by Blackcabs on 2008-09-09
> **ninjip said:**
> no good. it doesn't find the card. like if it didn't exist =/ 
Can you post the output of lspci this should show us something

---

