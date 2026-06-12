---
title: "Graphics card/driver problems"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by khaos28 on 2009-05-17
OK. so I'm new to Ubuntu, and with some help from a friend I've got almost everything up and running. The only thing that i;mn having problems with is a PCI input nVidia 6200 graphics card. I have thr driver all installed, but i can't run ubuntu through this specific card.

Well the only way i can get ubuntu to come up is in the low graphics version, with my on-board set as my primary adapter. Currently there are no other PCI slots being used, and the Card was working just fine yesterday before i put Ubuntu on my computer. But when i try to get Ubuntu to load with my card set as the primary adapter, it goes to the load screen and stops maybe 10% of the way, it freezes here and just doesn't move past it. I have tried recovery mode as well, but the code that comes up on the black screen also freezes as well.

---

### Post by khaos28 on 2009-05-17
Bump

---

### Post by Terry of Astoria on 2009-05-17
In recovery mode, does it really freeze, or dos it drop you to a prompt, where you can type commands?

---

### Post by sideffects on 2009-05-18
> **khaos28 said:**
> OK. so I'm new to Ubuntu, and with some help from a friend I've got almost everything up and running. The only thing that i;mn having problems with is a PCI input nVidia 6200 graphics card. I have thr driver all installed, but i can't run ubuntu through this specific card.

Well the only way i can get ubuntu to come up is in the low graphics version, with my on-board set as my primary adapter. Currently there are no other PCI slots being used, and the Card was working just fine yesterday before i put Ubuntu on my computer. But when i try to get Ubuntu to load with my card set as the primary adapter, it goes to the load screen and stops maybe 10% of the way, it freezes here and just doesn't move past it. I have tried recovery mode as well, but the code that comes up on the black screen also freezes as well.

From what you've told me, when you click on hardware drivers, the Nvidia one isn't active, so here is what I suggest. First, activate the Nvidia driver, then it will prompt you for a reboot. Do that reboot, but keep the onboard graphics card enabled in the BIOS (i.e. don't go into the BIOS and change anything.) When you login to Ubuntu, check to see if the driver is active (there will be a green light next to it.) If it is active, then at that point go ahead and reboot your pc, and this time change you graphics cards in the BIOS to enable the PCI Nvidia 6200.

---

### Post by khaos28 on 2009-05-18
> **sideffects said:**
> From what you've told me, when you click on hardware drivers, the Nvidia one isn't active, so here is what I suggest. First, activate the Nvidia driver, then it will prompt you for a reboot. Do that reboot, but keep the onboard graphics card enabled in the BIOS (i.e. don't go into the BIOS and change anything.) When you login to Ubuntu, check to see if the driver is active (there will be a green light next to it.) If it is active, then at that point go ahead and reboot your pc, and this time change you graphics cards in the BIOS to enable the PCI Nvidia 6200.

I tried that and i still got the same message saying that there is another version of this driver installed. I've tried updating it over and over but i keep getting the same thing, Either way, i re0installed ubnutu, and i didnt have it recognize my graphics card so i'm running in regualr defin (not low detail) and i have the stuff running, So i guess until there is an update that allows me to fix this, i'll just use my onboard.

---

### Post by khaos28 on 2009-05-18
And yes, that means i have some of the cool graphical stuff working, i'm still seeing what limits i can push to get the best, most comfortable feel of ubuntu. 

And for the most part, ti's a lor of stuff i can do :)

---

