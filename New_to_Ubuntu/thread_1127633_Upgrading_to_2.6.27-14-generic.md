---
title: "Upgrading to 2.6.27-14-generic"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by demarshall on 2009-04-16
I thought that I had installed 2.6.27-14-generic a few days ago but it didn't appear in Grub when I started my computer. Today it was offered as a new kernel again but again failed to be added to Grub. Since I'd like to be running the newest kernel that I have installed I added it using KGrubEditor which is on the main menu in System Tools.I created the new entry by copying the settings for the previous kernel and after running uname -a it shows that I am indeed running the new kernel.  :-))

Does anyone see any problems with what I did? Any comments?

---

### Post by zvacet on 2009-04-16
How many kernels do you have installed?If it is more then two you can unistall others going in synaptic and type linux-image and delete ones with lower number.Leave two kernels just in case that latest doesn´t work as you want to.

---

### Post by NeilMonday on 2009-04-16
I think what you did should be fine. It is strange how it wouldn't automatically update your grub though. Is your install mostly stock, or is it heavily customized?

---

