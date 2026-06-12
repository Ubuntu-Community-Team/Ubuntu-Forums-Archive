---
title: "has anyone managed to get WOW working on Vbox"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2009-03-19
as the title suggests I want to run WOW on a Virtual box.
Host is ubuntu 8.10
Virtual box version 2.1.4
Guest windows XP SP3

I get an error message saying "Failed to find a suitable video adapter"
whenever I try to run the game. Anyone got a solution

I did hear that the Vbox acceleration is better with openGL at the moment.
Any way I can force WOW to use that.

---

### Post by aeiah on 2009-03-19
WoW works well under wine, i dont think it's really necessary to use an entire virtual machine to run it. do you have any reason not to run it under wine or are you just finding out what works best?

---

### Post by billgoldberg on 2009-03-19
It won't work in a VM.

---

### Post by LowSky on 2009-03-19
VM has no support for graphics cards. sorry your out of luck with that


WoW does work very well with Wine
to install use add/remove or synaptic, or open a terminal and type this

sudo apt-get install wine

---

### Post by Rinulin on 2009-03-19
My understanding is that WoW won't run in a VM because the VM cannot use the 3d graphics necessary to run WoW. Basically, you can't run any 3d game in Ubuntu via a VM.

Wine works very well, however (as was mentioned before). When I had WoW running in Ubuntu, I actually got better FPS and Latency than on Windows XP.

---

### Post by Skol312000 on 2009-03-19
Wow = equals. Worle of warcraft ?  Or. Call of duty ...World at War?

---

### Post by Malalo on 2009-03-19
> **Skol312000 said:**
> Wow = equals. Worle of warcraft ?  Or. Call of duty ...World at War?

Wouldn't World at War be WaW instead of WoW ?

---

### Post by LowSky on 2009-03-19
> **Malalo said:**
> Wouldn't World at War be WaW instead of WoW ?

This is Why I hate when people use abbreviations, if people see that and are not gamers they might not know, this applies to any programs. Say the name and then use the abreviation, that way there is less confusion.

 WoW is World of Warcraft. World at War is CoD:WaW, only because it is a Call of Duty sequel.

---

