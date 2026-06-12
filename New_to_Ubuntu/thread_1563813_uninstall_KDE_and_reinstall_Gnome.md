---
title: "uninstall KDE and reinstall Gnome"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by Syd Martin on 2010-08-29
Hi, I've been a plonker :confused:again!

I have run **sudo apt-get install kubuntu-desktop**  to see if I liked the KDE desktop.

I like Kontact and think I could get used to it and perhaps find it useful **BUT** I want my Ubuntu Gnome back and don't know how to do it.

Also if I want to uninstall Ubuntu and remove the partition with Windows can someone tell me how. Then I can format the harddrive and reinstall Ubuntu on a clean drive.

This may seem simple to some, but to this old man it is proving to be a real headache.

Cheer,

Syd Martin:(

---

### Post by davidmohammed on 2010-08-29
the opposite to sudo apt-get install is sudo apt-get remove

- you should be able to 

sudo apt-get remove kubuntu-desktop.

If you just want a clean install, slip in your 10.04 desktop CD and during the install you'll be asked about partitioning.  Select the option "use the entire disk".  This will erase windows and all previous partitioning.

---

### Post by howefield on 2010-08-29
> **Syd Martin said:**
> I want my Ubuntu Gnome back and don't know how to do it.

It hasn't gone away, you can switch the desktop environment from your login menu. (Although your menus may still have mixed kde/gnome apps).

> Also if I want to uninstall Ubuntu and remove the partition with Windows can someone tell me how. Then I can format the harddrive and reinstall Ubuntu on a clean drive.

Watch some of the screencasts at screencasts.ubuntu.com eg,

[http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)
[http://screencasts.ubuntu.com/2009/08/25/Ubuntu_Live_Installer_Boot_Screen](http://screencasts.ubuntu.com/2009/08/25/Ubuntu_Live_Installer_Boot_Screen)

Then ask any questions you might have, they are all short videos.

---

### Post by jotlims on 2011-03-19
I have also installed Kubuntu along with my ubuntu. If I sudo the Kubuntu will it mess up my apps?

---

### Post by leviathan8 on 2011-03-19
> **Syd Martin said:**
> Hi, I've been a plonker :confused:again!

I have run **sudo apt-get install kubuntu-desktop**  to see if I liked the KDE desktop.

I like Kontact and think I could get used to it and perhaps find it useful **BUT** I want my Ubuntu Gnome back and don't know how to do it.

Also if I want to uninstall Ubuntu and remove the partition with Windows can someone tell me how. Then I can format the harddrive and reinstall Ubuntu on a clean drive.

This may seem simple to some, but to this old man it is proving to be a real headache.

Cheer,

Syd Martin:(

You can simply log out from the current session, and once you are in GDM, select your user, go to bottom and look for a button that lets you choose your desktop environment (you will see something like xterm, GNOME failsafe, GNOME, etc.).
Instead of just uninstalling ubuntu, you could use GParted to delete the Windows partition (usually /dev/sda1 [don't forget to look after it's size and filesystem format (NTFS)]), then create a new ext3 partition with the unallocated space left. After this, the most important part is that you run **sudo update-grub**, so grub.cfg is updated and it won't mess up during the boot time. You may notice that you won't be able to read or write anything on the freshly created ext3 partition. To do this, simply mount your new partition, open from a terminal **gksu nautilus**, go to filesystem -> media -> your-new-partition-name (usually the UUID is displayed - many random characters - or XX.X GiB Filesystem) right click on it -> properties -> permissions -> set owner and group to your username and give it the ability to create and delete files. After that, all you would like to do is to set a label for the new partition. Unmount it, open baobad and Set Label on the newly created partition.

> **jotlims said:**
> I have also installed Kubuntu along with my ubuntu. If I sudo the Kubuntu will it mess up my apps?

It will only delete everything that came with kubuntu-desktop (kde applications, dependencies, etc.).

---

### Post by milindo on 2011-03-19
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Follow this and you'll have kde out in no time

---

### Post by jotlims on 2011-03-19
Thanks

---

