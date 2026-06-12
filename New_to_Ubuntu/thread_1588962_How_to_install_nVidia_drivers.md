---
title: "How to install nVidia drivers?"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Lerhond on 2010-10-05
Hello!
I have a SONY VAIO VPCF12M1E notebook with nVidia GT330M graphic card. I want to know how to install nVidia drivers on my computer. I have Kubuntu 10.04.1. I didn't do anything on it - it was just installed (any upgrades etc.). If it's possible I don't want to install it manually, but using repo. I tried several times but I can't do it. If it's possible, I want to use only Console to do anything, because without this drivers I don't see some part of the screen and I can't use system normally.
Thank you for your help.
Sorry for my bad English.

---

### Post by kaldor on 2010-10-05
Navigate to K Menu > Applications > System > Hardware Drivers and you should be able to take it from there :)

If you have issues, please post back!

Edit: This is the Official/"Ubuntu" way of installing the drivers. They will be enabled and may be updated the same way as other applications. Not really any need to use the console.

---

### Post by Lerhond on 2010-10-06
Hello!
I turned on this nVidia driver with this Hardware Drivers tool and then I rebooted my computer using ```
sudo reboot
``` (without drivers I can't see part of the screen and using K Menu is hard, so I did it with Console). Now I have a problem without turning on my computer - the graphics don't appear. Becouse I don't know how to describe the problem, I give you a video what show what is happening when I turn on my Kubuntu. You can download it here:
[http://www.wrzuc.to/6W8hRxf1BF.wt](http://www.wrzuc.to/6W8hRxf1BF.wt)
At the end I turn off it using POWER button, becouse nothing happens (also when it'll stay for some time) and there's a black screen.
Maybye after Kubuntu installation I should update what is possible? I installed the drivers immedetialy after installing of Kubuntu.
Thank for your help and I hope you will answer.

---

### Post by cgroza on 2010-10-06
So you get a black screen after Kubuntu finishes booting. This kind of problems were solved by editing the kernel boot line.

---

### Post by Lerhond on 2010-10-06
Yes, I get black screen, but:
1. What I need to edit?
2. Before getting a black screen the graphical interface didn't load. :/

---

### Post by cgroza on 2010-10-06
I really don't know, but I saw threads around that solved this issue. All I can remember is something about adding "nomodeset" at the end of the kernel line. You can access the kernel line by pressing "e" at that screen where you choose the kernel.

---

