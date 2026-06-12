---
title: "Can't find /boot/grub/menu.lst"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Pikachuu on 2010-01-15
I just tried to clean up my grub bootloader since it's become very cluttered, but I couldn't follow this guide: [http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/) because I can't find the /boot/grub/menu.lst. I went through the terminal and couldn't find it and also copypasting the command from the guide gives me a new blank file in gedit. Any help would be appreciated. :D

---

### Post by lisati on 2010-01-15
Did you install 9.10 from scratch or did you upgrade from an earlier version? 

9.10 uses grub2, which is organized differently.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by ranch hand on 2010-01-15
If you are running grub-legacy (grub0.97) then the /boot/grub/menu.lst is easy to get to;
```

gksudo gedit /boot/grub/menu.lst

```

If you are running grub1.97beta4 then you should start by reading my post in the link in my sig.  The second link that I have in that post is probably the best grub2 info you are going to find.

To find the version you have;
```

grub-install -v

```
will tell you.

I really wish that folks would get there information with in the community first rather than outside.  It is generally more up to date and written by folks who have actually seen the app they are writing about and probably have even used them.

---

### Post by Pikachuu on 2010-01-15
Wow, thanks for the quick replies. I had grub1.97beta4 which I assumed to be the legacy version since I'd heard about a grub2 somewhere. Thank you for the links, they helped a lot. :3

---

### Post by mikewhatever on 2010-01-15
> **Pikachuu said:**
> Wow, thanks for the quick replies. I had grub1.97beta4 which I assumed to be the legacy version since I'd heard about a grub2 somewhere. Thank you for the links, they helped a lot. :3

Actually, no, grub1.97beta4 is grub2. Regardless, instead of simply removing entries from the menu, I'd suggest uninstalling the unneeded kernels, which will also take care of the menu. To do that, search for linux-image in Synaptic. Make sure you don't remove the latest version.

---

### Post by ranch hand on 2010-01-15
1.97beta4 is the new grub (grub2).  I have no idea why the buggers don't put in a newer version.  In 10.04-testing we are using grub1.98, I have grub1.97 (no beta4 hooked to that) on my 9.10 install.

Deleting old kernels is a good idea.  Some folks like to keep one back.  

I would concider teh symbolic menu entries in a custom file and make the /etc/grub.d/10_linux, 20_memtest86, 30_os-prober and 40_custom non-executable (assuming that your custom file is 06_custom).

Those entries never need updated as they boot to the newest kernel on the defined partition.  It is all I use for all Debian based OS' (I have 12 OS' on my test platform one with a symbolic entry that is different for Mandriva).

---

### Post by mikewhatever on 2010-01-15
12 OSs? How many times a day do you reboot?

---

### Post by ranch hand on 2010-01-15
I have one Lizard (I know that the Ubuntu people think that 10.04 is called Lucid Lynx but some of us know that it is Lounge Lizard) that I use as my production OS in the day time.  It has an alpha version of boinc running on it that keeps the cpus cranked to 99 - 100% all the time.

I chroot into the other OS' and update them from there (not updating the one I use until is see what they do to the others).  about once a day I can fliy through hand do what I need on the others.  Most of them have some experimental thing on them that could crash the system.  If you have them all on one pre-release OS you have no ide a what screwed the thing.

One of them is Zenix.  It is an Ubuntu 9.10 respin that uses Xfce.  Check it out.

Mandriva 2009-1 is really neat to0 and I am sure the newest one is too, if you can stand rpms.  LiveDVD with your choice of Gnome, Lxde, and KDE and you can install one or however many you want.  I have them all on there but never open the KDE because I am not compatible with it (hate it).

But, back to the question, it depends on the day and how many installs of the Lizard are broken (I have only 7 of them).

---

### Post by kansasnoob on 2010-01-15
Ranch hand's a blacksmith. He likes to hammer things :D

I'm a mechanic, I like to try and fix things and then throw them across the shop :D

---

### Post by ranch hand on 2010-01-15
With a BIG hammer.

---

### Post by mikewhatever on 2010-01-15
Why Lizard? Anything wrong with it?

---

### Post by Paqman on 2010-01-15
> **ranch hand said:**
> 
Deleting old kernels is a good idea.

+1

This is the easiest way to clean up most of the mess Grub gets in, and has the added bonus of freeing up 100MB of drive space per kernel removed.

If you can't remember which kernel you're running, then you can find out with:
```
uname -r
```

The just open up Synaptic and search for "linux-image" and remove all the old versions you're not using (and maybe a spare if you're paranoid). Make sure you keep linux-generic, otherwise you'll miss out on updates.

Removing the old kernels automatically removes them from Grub.

---

### Post by ranch hand on 2010-01-15
Wrong with it?  Heck no.  Runs great, right now, on my hardware.

Why lynx?  Does it sneak around and pee on everything it comes across (nope I am not a cat lover).

9.10, by the way should be known as Kinky Kitty.

I am real new to Ubuntu and Linux.  My first experience was just before the introduction of 8.10 (see join date) with Horny Horse (8.04).

It is my box and I can call them anything I want.

---

