---
title: "Intel wireless pro 4965AGN"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by 2Fac3 on 2008-07-23
Hi, I bet you haven't heard this before but I'm new to Ubuntu. I'm using a built-in Intel pro 4965AGN wireless card. When I first installed Ubuntu it auto detected and installed the drivers, but I tried to update the drivers and ended up uninstalling them and now I cant figure out how to reinstall the drivers. I've been fiddling around with it for an embarrassingly long time. If someone could please tell me how I can go about reinstalling the drivers without having to complete reinstall Ubuntu that would be awesome!

---

### Post by chili555 on 2008-07-23
> I cant figure out how to reinstall the drivers.It's relatively easy. When you boot your computer, you will notice a reference to GRUB and a three second countdown. Before the three seconds elapses, press Esc and the GRUB menu will appear. Use the arrow keys to highlight an older kernel than the one you are using now. For instance, my running kernel is 2.6.24-19-generic, so I might wish to boot into a previous kernel, 2.6.24-**18**-generic, for example. Press 'b' to boot into the previous kernel.

Once you are booted up and logged in, go to System -> Administration -> Synaptic and search for linux-image. Find the latest kernel installed, indicated with the green box, right-click it and mark it for re-installation. Press apply and let it hum. All the modules you removed or modified will be re-installed. Configuration files, most commonly in /etc will *not be *changed. 

Reboot and you are all set.

---

### Post by 2Fac3 on 2008-07-24
First off chili555 thank you very much for the quick response. :D

What you said make complete sense, but when I pull up the grub menu I only have two kernels to choose from  2.6.24-19-generic & 2.6.24-19-generic(recovery)
 
I booted up the recovery kernel but was unable to get a GUI I tried alt-control f7 but no luck. I'm sure its possible to reload the kernel using the console but I haven't the slightest clue where to start.

---

### Post by chili555 on 2008-07-24
I don't know if you can re-install the kernel you are actually running, either in recovery mode or not. I'm not anxious to find out that you can't.

I would boot into -19, open Synaptic and search for *linux-image.* See if you have the option to install **-18**. Then reboot, go into the GRUB menu and boot into -18 and, in Synaptic, re-install -19.

---

### Post by 2Fac3 on 2008-07-24
I don't have the option to install 2.6.24-**18**-generic but maybe I could use a different kernel image like 2.6.15-52-server or 2.6.15-52-686

Would something like that do the trick? I wanted to check first before potentially damaging my situation further.

---

### Post by chili555 on 2008-07-24
It will be fine. Try to find a -generic.

---

### Post by 2Fac3 on 2008-07-24
It took a little tweeaking but that worked TYVM chili555 :)

---

