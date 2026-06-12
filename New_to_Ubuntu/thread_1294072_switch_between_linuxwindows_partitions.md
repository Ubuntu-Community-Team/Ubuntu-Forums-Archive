---
title: "switch between linux/windows partitions"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by community nerd on 2009-10-17
Ok here is my scenario. I am trying to set up a friends computer with quickbooks, an accounting program. It is the 2009 version. That wont install. I resized my hard-drive from 140 gb to 100gb and installed windows on that. I did use the livecd and did the grub MBR re-installation but all that did is to cause linux to start up instaead of windows with no trace of windows. If you hit esc as it is booting it gives you the kernel versions but no windows. Any one know how to fix it. If there is a free linux business accounting program would you let me know?

---

### Post by mike555 on 2009-10-17
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)

---

### Post by community nerd on 2009-10-17
Thankyou

---

### Post by Mark Phelps on 2009-10-18
You asked about Wine ...

The link below is to the page on the CodeWeavers (supplier of Wine) Application Compatibility database for quickbooks.  Most of the versions are rated Garbage -- meaning, they most probably will NOT work: 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=120]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=120")

---

### Post by cariboo on 2009-10-18
I would suggest you install Windows in a vm using Virtualbox, as I have seen comments elswhere in the forums that Quickbooks 2009 will not work in Wine. 

You can run Windows in Virtualbox in seemless mode, and it will seem as if you are running Windows natively.

Virtualbox is in the repositories.

---

### Post by oldfred on 2009-10-19
When you install windows after linux, besides the grub update you have to add the windows entry to menu.lst.

Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

I do not know if grub legacy (old grub) will find windows with the update-grub. (new grub2 does)

This is to automatically generate a new menu.lst file for you.
sudo update-grub

If it does not you have to add a new entry:
gksudo gedit /boot/grub/menu.lst

In a terminal run fdisk -l to see what partition windows is in. Grub counts from zero so sda1 is (hd0,0), adjust entry below to your partition and adjust title to whatever windows you have. Title is just what you see on the menu when you reboot:

title        Windows Vista (loader) on sd[COLOR=DarkRed]a2[/COLOR]
rootnoverify    (hd0,[COLOR=DarkRed]1[/COLOR])
savedefault
chainloader    +1

---

### Post by romankarlfranz on 2012-05-09
hi. i just installed windows 7 on an extra partition on my hd and now it loads windows by default. how can I switch/choose between linux mint 12 and windows installation?
i did no grub backup or anything. I really dont know how that works. What can I do now? Thanks.

---

### Post by cryptotheslow on 2012-05-09
Follow the guide here to reinstall the GRUB2 bootloader.

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by oldos2er on 2012-05-09
Old thread closed.

---

