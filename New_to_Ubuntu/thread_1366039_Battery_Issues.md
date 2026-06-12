---
title: "Battery Issues"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Linux_Man on 2009-12-28
Ok, I have Ubuntu 9.10 and a Toshiba Satellite L305-S5955, and I have power management set to reduce screen brightness when it is unplugged and increase it when its plugged in. However, it does not. If I start my computer plugged in, it keeps the power profile for it running on AC power, if I start the computer with it on battery power it keeps that profile. Plugging it in charges the battery and unplugging it discharges the battery. 


So is this a bug in Ubuntu, a flaw in my hardware or is this just a feature and not a bug?

---

### Post by Linux_Man on 2009-12-28
Ok, I also created a new account and did the same thing and got the same result. So I'm not sure if its a configuration issue now.

---

### Post by mark.altern on 2009-12-28
the gnome-power-manager is NOT working very well for me, either. Specifically, it sometimes works, sometimes not. Eg, the screen will dim sometimes, and sometimes it will just keep the full brightness when switching to battery from AC power. 

I have not be able to figure out what was wrong, guess it is about some acpi configuration files, in my case, it is different, since I use the thinkpad_acpi driver. 

But, now I simply ignore it, manually change the brightness when necessary is not too bad any way.

---

### Post by Linux_Man on 2009-12-28
Yeah, I think I'm just going to have to ignore it too. At first I was worried that it was a hardware issue but since it works fine in Windows and everything, I have to say its a bug in Gnome power manager

---

