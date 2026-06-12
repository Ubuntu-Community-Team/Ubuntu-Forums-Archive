---
title: "Wireless In Ubuntu"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by mwiebelhaus on 2007-04-29
I recently installed dual boot with xp media and ubuntu but in ubuntu it dosent have a driver for my intel pro wirless card. can i use the driver for linux off of the intel site?

Intel(R) PRO/Wireless 3945ABG Net

also i know nothing about lunix so when they have all these weird things to install like something to do with % i dont even know what to do i want to get the internet working first.

---

### Post by Thomi on 2007-04-29
> **mwiebelhaus said:**
> I recently installed dual boot with xp media and ubuntu but in ubuntu it dosent have a driver for my intel pro wirless card. can i use the driver for linux off of the intel site?

Hi, I also have an Intel PRO/Wireless ABG card, and I have similar problems. Perhaps if you are able to identify the *exact* card / chip you have that would help (for example, I have an Intel Pro Wireless 3945).

Also, how do you know it doesn't have the correct driver? How are you testing it? 

Generally, posting the output of the lspci command helps to identify the hardware type & version, and the 'lsmod' prinds a list of kernel modules (i.e.- drivers) currently loaded in the kernel.

If you're able to give us this information that would make helping you a lo easier.

Thanks!

---

### Post by Suzan on 2007-04-29
I have an Intel Pro Wireless AGB 3945 also. It works with Feisty out-of-the-box.

The driver is included in the restricted-modules.

---

### Post by mwiebelhaus on 2007-04-29
i have that wireless card the intel pro wirless abg i will get exact code of it in a sec but i know thats the one it is

---

### Post by mwiebelhaus on 2007-04-29
nvm in just going to install feisty hopefully it works

---

