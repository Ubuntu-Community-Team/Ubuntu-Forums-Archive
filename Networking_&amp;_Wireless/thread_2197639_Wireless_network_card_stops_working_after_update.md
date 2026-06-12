---
title: "Wireless network card stops working after update"
date: 2014-01-04
forum: Networking &amp; Wireless
---

### Post by darwall on 2014-01-04
Hi!
I have a computer with Xubuntu 12.04 with a D-Link wireless network that works great.
But every time I run an update, the wireless network card will stop working.
The first time it happened, so I Googled for days before I found the solution.
The solution is to run these commands:
"cd Desktop/rt5370/
sudo make
sudo make install
sudo modprobe rt5370sta"
Then it worked again for a while.
But next time there were updates so the same thing happened again.
But this time I did not have to look that long after the solution.
By now I run these commands automatically when the card stop working after an update.
Does anyone have any idea what the cause might be, or if there is no solution so I do not have to run these commands after each update?
Very grateful for advice
Sven from Sweden

---

### Post by wildmanne39 on 2014-01-04
With this kind of driver any time their is an update to the kernel you will have to recompile the driver it is the way it is made, if the driver can compile with dkms then it would automatically do it itself after a kernel update but I believe that has to be written into the driver.
Thanks

---

### Post by Leechpool on 2014-01-04
Hi,
I hesitate to answer because I'm no expert but ......
If the driver required to run a piece of hardware is built into the kernel or an unbuntu packaged module e.g. installed through synaptic / software centre, then it will get updated to match the kernel if the kernel is updated as part of an update.
It sounds as if you have manually downloaded the driver you require for your network adapter and compiled the source. This makes a module (driver) but only for the kernel running. Whenever the kernel is updated e.g. as part of a software update, you need to recompile the module which is what the commands sudo make etc. are doing. This is quite normal and many people live with it when using hardware with "externally" provided drivers. I have the same issue with a DVB TV card. It may be the case that there is an ubuntu packaged version of the driver you require which would be automatically updated but you'd need to check.
There does appear to be ways to make externally obtained drivers recompile automatically but I've never tried it.
This link [http://askubuntu.com/questions/249509/how-does-updating-the-kernel-affect-custom-modules]("http://askubuntu.com/questions/249509/how-does-updating-the-kernel-affect-custom-modules") is about someone asking a similar question and the answer describes a method using [DKMS]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support") to automatically recompile the module when the kernel is updated.
Hope this helps.
:P

---

### Post by darwall on 2014-01-08
Thanks so much for your reply.
Well that's correct, I have manually downloaded and installed the driver.
It's probably a little too advanced for me. I can not such things as compilation. I thought that perhaps there is a quick fix, but I can live with this problem.

In a few months there will be a new LTS version of Ubuntu. Then maybe they've fixed so that the driver is built into the kernel.
Well, again, Thanks for your reply.

---

### Post by praseodym on 2014-01-08
Which driver version is it? 2.5.0.3? If yes, here is the dkms installation:```


sudo apt-get install --reinstall linux-headers-$(uname -r) [COLOR="#FF0000"]linux-headers-generic[/COLOR] build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/42/20/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA 
```
Check the kernel with
```

uname -a
```for the right metapackage of the kernel-headers (marked in red).

List of supported cards here (grey boxes):

[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/#Liste-unterstuetzter-Geraete](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/#Liste-unterstuetzter-Geraete)

---

