---
title: "Grub Bootloader, 64-bit upgrade, and much more.."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by designateduser on 2009-08-19
Hey Community!
So today I have a couple of questions:
1. Whenever I start my computer and grub boot-loader starts it shows all the kernel updates, and I am only using the one that is most recent (updated today:P) so how can I get rid of all of these? [http://s856.photobucket.com/albums/ab122/desiganteduser/?action=view&current=0819091321.jpg](http://s856.photobucket.com/albums/ab122/desiganteduser/?action=view&current=0819091321.jpg)

2. My processor is an AMD 64-bit processor and I have over 4 gigs of RAM, so should I upgrade to Ubuntu 9.04 (or other variant) 64-bit? I accidentally installed the 32-bit jaunty jackalope and it is currently duel booting with windows visa (yuck!) so how could I install a third operaterating system and then get rid of my 32-bit version?

3.I know there must be a simple awnser to this one but how do I make it so when I sign in a program called "cario dock" runs? I tried to add it to system>pref>startup apps but I did not know the command for it.

If you can help me with any of these it is much apprecieated! Long live linux (lol)!

---

### Post by Ichtyandr on 2009-08-19
1. try removing old kernels from synaptic, look here: [http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

2. 64 bit: AFAIK you cannot upgrade, but have to reinstall

3. Go to "System", "Preferences", Startup-Applications and add there "cairo-dock"

PS
try gnome-do docky for an excellent docking in gnome (but install the latest version from PPA, it is less buggy than one in universe repo)

---

### Post by sreenath on 2009-08-19
> **designateduser said:**
> Hey Community!
So today I have a couple of questions:
1. Whenever I start my computer and grub boot-loader starts it shows all the kernel updates, and I am only using the one that is most recent (updated today:P) so how can I get rid of all of these? [http://s856.photobucket.com/albums/ab122/desiganteduser/?action=view&current=0819091321.jpg](http://s856.photobucket.com/albums/ab122/desiganteduser/?action=view&current=0819091321.jpg)

2. My processor is an AMD 64-bit processor and I have over 4 gigs of RAM, so should I upgrade to Ubuntu 9.04 (or other variant) 64-bit? I accidentally installed the 32-bit jaunty jackalope and it is currently duel booting with windows visa (yuck!) so how could I install a third operaterating system and then get rid of my 32-bit version?

3.I know there must be a simple awnser to this one but how do I make it so when I sign in a program called "cario dock" runs? I tried to add it to system>pref>startup apps but I did not know the command for it.

If you can help me with any of these it is much apprecieated! Long live linux (lol)!

1. Do you want to uninstall the old versions or just remove them from the menu?

2. I would recommend sticking with 32 bit. Lots of applications and drivers that work on 32 bit do not work on the 64 bit version.

3. The command to run cairo dock is cairo-dock.

---

### Post by ptn107 on 2009-08-19
1) A good rule of thumb is to keep your current working kernel and at least one backup.  So I would keep 2.6.28-15 & 2.6.28-14.  You can remove kernels with this command in a terminal:
```
sudo aptitude purge linux-image-2.6.28-14-generic linux-image-2.6.28-13-generic linux-image-2.6.28-11-generic linux-headers-2.6.28-14 linux-headers-2.6.28-14-generic linux-headers-2.6.28-13 linux-headers-2.6.28-13-generic linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic linux-restricted-modules-2.6.28-14-generic linux-restricted-modules-2.6.28-13-generic linux-restricted-modules-2.6.28-11-generic -y
```

2) Unfortunately you cannot upgrade from 32 to 64 bit.  A clean install is required.

3) The command is located at /usr/bin/cairo-dock but an entry should have been made for you under Applications -> System Tools.

---

### Post by designateduser on 2009-08-19
Solved! thanks!

---

### Post by sreenath on 2009-08-19
> **designateduser said:**
> 2. My processor is an AMD 64-bit processor and I have over 4 gigs of RAM, so should I upgrade to Ubuntu 9.04 (or other variant) 64-bit? I accidentally installed the 32-bit jaunty jackalope and it is currently duel booting with windows visa (yuck!) so how could I install a third operaterating system and then get rid of my 32-bit version?

If you want to install a 64 bit version, first back up all of the files you want to keep, then boot with the 64 bit install CD. Before installing, use gParted to delete your old partition. Then install the 64 bit version.

---

