---
title: "Battery not recognized on my laptop (and it recognizes my laptop as a desktop)"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Crammedshelfish on 2011-04-16
I have installed Ubuntu (both 10.10 and 11.04 pre-release) on my laptop but my battery is not recognized and it is detected as a desktop system rather than a laptop. I have tried the cat /proc/acpi/battery/BAT1/state method but the directory doesn't exist. I have tried another guide to paste the battery info into this directory but it doesn't allow me to do that and says that the directory doesn't exist, even though I'm trying to make it. I tried it in root nautilus and even on an install of Lubuntu (with a root file manager) but it still failed to budge. I really don't know what to do as I have tried all the guides on the internet that I could find.

Thanks in advance.

AZorin

---

### Post by KegHead on 2011-04-16
Hi!

Try:

software center..type in battery.

KegHead

---

### Post by cmcanulty on 2011-04-16
Check sys-prefs -power man and be sure it is checked to show battery usage. I think desktop is just the system not specifically desktop or laptop

---

### Post by oklokl on 2011-04-16
Instability bug..

---

### Post by Crammedshelfish on 2011-04-17
Thanks for the reply cmcanulty!
The sys-prefs -power man command didn't return anything, it says command not found. When I try to look up sys-prefs in Synaptic it doesn't show up anything. 
Ubuntu recognized my computer as a desktop during the installation process when it usually finds the computer's name or if it's a laptop or desktop and names the computer after that in the Who are you step. 
Gnome power manager also only shows up the On AC Power tab.
Thanks!

---

### Post by Crammedshelfish on 2011-04-18
Anyone?

---

### Post by Crammedshelfish on 2011-04-19
bump

---

### Post by Crammedshelfish on 2011-04-19
Bump

---

### Post by Crammedshelfish on 2011-04-21
bump

---

