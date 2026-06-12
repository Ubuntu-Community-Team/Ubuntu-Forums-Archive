---
title: "Senao NL-2511CD+ext2 (Prism2.5 chipset) ---  not working"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by BenDover on 2005-09-07
hi all

I've been trying to get this card working on my Asus z92u laptop... but no success so far...
it's not autodetected as i hoped, dont know why though... I bought this card because of its Linux support ;) 
tried it with different live cd's first (WHAX, Auditors) -- no luck
I've installed Ubuntu dvd now, hoping it would support it :(

what i tried so far:
install HOSTAP driver, but no luck, it needs the source code or something to build the driver? 
(plz dont mind my n00bness, i'm learning ;)
my pcmcia slot is detected, but nothing happens when i insert/eject the card..

some help would be greatly appreciated!


/edit: forgot to mention: its working great under XP, but using windows is my only way to get online (so far... )  so any apt-get commands wont work, i can download drivers/stuff in windows, reboot, and continue from there :)

---

### Post by daageep on 2005-09-18
i'm not using ubuntu currently (debian 2.6.11 kernel) but ubuntu *should* have a package called hostap-modules-2.6.8.X... hmm now that I check, the modules are only available for 2.6.8 which i don't think ubuntu has. 

i think you can install the hostap drivers the following way:
1) go to /usr/src and make sure you have the kernel-headers in there. suppose you have kernel 2.6, make sure there's a folder called kernel-headers-2.6 in /usr/src.
2) then go to /lib/modules/`uname -r`/ and use ls -l to look for the build link. next to "build" you should see it pointing to /usr/src/kernel-headers-2.6
3) if you don't have the kernel-headers from 2), do an apt-get install kernel-headers-`uname -r`
4) if you don't have the build link in the /lib/modules/2.6 folders, do sudo ln -s /usr/src/kernel-headers-`uname -r` build
5) sudo apt-get install hostap-source. this should be installed in your /usr/src folder. then apt-get module-assistant. configure the module by doing sudo m-a build -t hostap. it will build the module automatically for you and spit out any error messages.
6) if you don't have any errors, there should be a .deb file in the current folder. to install, do sudo dpkg -i hostap.deb

this will install hostap drivers for you =)

but that's weird that your card is not supported. i have a 2511cd plus (internal antenna) and whoppix/whax/auditor/debian picks the card right up (not the driver, but at least cardctl ident shows the card). 

are you sure it's not an M edition? M stands for mercury and looks exactly the same as the 2511. it's a prism3 and has slightly different information when you run cardctl ident. you have to add something to /etc/pcmcia/config or else ubuntu will not load the right modules.

hope this helps :)

---

