---
title: "Atheros+Ibex+Network Manager"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by jmasgalas on 2008-11-06
I just freshly installed Ibex hoping wireless would be easier by now. I have an Atheros AR5001X+ wireless card. I followd the instructions I saw somewhere here to disabled the default driver and use the ath5k driver. I rebooted and looked in Hardware Drivers and it says that the 5xxx driver is active and in use. However when I right click network manager Enable Wireless is greyed out. When I left click NM it shows the drivers but under then it says Wireless is disabled.

How can I enable wireless? I am trying to connect to a LEAP network.

---

### Post by jmasgalas on 2008-11-14
bump. Anyone?

---

### Post by AlanR8 on 2008-11-14
I had a similar issue when I put Ibex on my EeePC. I don't know if the wireless card is the same as yours but you could try the following.

I can't take credit for the content as it came from these hallowed forums. When I find a useful post I copy and paste it into a word processing document and keep it for future reference. PLEASE backup any files before modifying as a precaution.

First off you have to edit a file as follows:

> sudo vi /etc/modprobe.d/blacklist

and append,

blacklist ath_pci
blacklist ath_hal


Depends what editor you use, I use Kubuntu so the command was sudo kate /...........

You could reboot at this stage and see if the wireless works. If not, try this:

Open a terminal and paste the following:

> sudo apt-get install linux-backports-modules-intrepid


Now reboot and hopefully the wireless will work. It did on my EeePC and I had to use both steps.

---

### Post by jmasgalas on 2008-11-17
That did not work. When I left click Network Manager wireless is still disabled. Under Hardware Drivers it does show Ubuntu using the 5xxx drivers. I am at loss as to what is going on.

---

### Post by AlanR8 on 2008-11-18
There's nothing more I can suggest.

I just borked my EeePC and had to do a fresh install last night (Kubuntu 8.10 with KDE 4.1.*).

All went smoothly. I did the install WIRED to the Web but then did my tweaks above as a first task, together with installing other favoured apps. Rebooted and the wireless worked a treat.

Sorry I can't be of more assistance.

---

### Post by jmasgalas on 2008-11-21
I also tried kubuntu with no success. OpenSUSe same thing. Finally I threw in the Fedora 10 Live CD and it worked like a charm. It detected my card and I was up and going in a few minutes. I think I will just leave my laptop with Fedora for now and use Ubuntu on my desktop.

---

