---
title: "Switching from Ubuntu to Kubuntu"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-03-30
Okay...currently I have Ubuntu 9.04 64 bit.  I want to repartition my hard drive and set myself up with Kubuntu 10.04 64 bit doing a fresh install.

I am wondering the best way to go about making sure I don't lose anything.  I already have full backups of all of my files, so I am not worried about my music/pictures/documents etc.  I have used a dpkg script to get a list of all of my currently installed applications.  I am wondering if I will be able to use that script to re-install all of my applications when I set up Kubuntu?  My understanding is that it is just using KDE vs Gnome for desktop environment, but should that affect my programs at all?

I also would like to know how to be sure I save my current theme/preferences for all of my applications.  Is that in the /etc folder and if I copy that will that be okay?  Or do I have to copy all of the .program folders from /home/user?

Lastly, I have some programs installed that aren't installed via terminal such as Maple 13 which I use for my engineering courses.  I have the installation files, so will I just have to reinstall that?  Or is there a way to do a full backup of my entire system and install all of my files and programs that way?

Any other thoughts/concerns/ideas are greatly appreciated as I have a month or so to figure it out and finalize my plans.  I will have a full image of my hard drive as it currently is too just in case anything doesn't go according to plan.

---

### Post by laidback on 2010-03-30
On the 32 bit system I have Ubuntu and Kubuntu on the same system, you can choose at boot up which desktop you want.

I think the Kubuntu add on to an Ubuntu install is called Kubuntu desktop, but check Synaptic to be sure.

---

### Post by x C0MMAND0 x on 2010-03-30
Okay...perhaps I should have worded my title more about migrating to a new version on a fresh install instead of an upgrade and the necessary steps needed to take to make sure I don't lose anything.

---

### Post by Paqman on 2010-03-30
> **x C0MMAND0 x said:**
> 
I am wondering if I will be able to use that script to re-install all of my applications when I set up Kubuntu?  My understanding is that it is just using KDE vs Gnome for desktop environment, but should that affect my programs at all?


It won't affect your apps at all, except that the new desktop environment will come with a different set of default apps. For exmaple, you won't have Gedit as your text editor any more, you'll have Kate.

The easiest way to do it is (IMO) just go through and make a list of all the apps you want to reinstall, then you can feed the list into APT when you reinstall.

For example:
```
sudo apt-get install pysdm startupmanager avant-window-navigator preload 
```

...would install Storage Devices Manager, Startup Manager, AWN and Preload all in one step.

> I also would like to know how to be sure I save my current theme/preferences for all of my applications.  Is that in the /etc folder and if I copy that will that be okay?  Or do I have to copy all of the .program folders from /home/user?

Your themes will be completely different. You settings all live within the .folders in /home/user.

> I have the installation files, so will I just have to reinstall that?

Yep. Although your settings will still be kept if you backed up /home/user.

When you restore all your settings from /home/user/.whatever, make sure you get the ownership right. If you set the user accounts up even slightly differently on the new system, you can end up with problems.

---

### Post by x C0MMAND0 x on 2010-04-01
> **Paqman said:**
> When you restore all your settings from /home/user/.whatever, make sure you get the ownership right. If you set the user accounts up even slightly differently on the new system, you can end up with problems.

How would I go about making sure all of the ownership / permission settings are correct?  I don't know if it will matter, but I will have the same username some /home/user will be the same.

---

### Post by x C0MMAND0 x on 2010-04-05
Any Ideas on how would I go about making sure all of the ownership / permission settings are correct? I don't know if it will matter, but I will have the same username some /home/user will be the same.

---

### Post by Maheriano on 2010-04-05
I have a separate question maybe I can quickly ask here.
Is there an easy way I can switch to KDE for a few days and then back again if I don't like it? Is it just a package to install? Thanks.

---

### Post by egalvan on 2010-04-05
> **Maheriano said:**
> I have a separate question** maybe I can quickly ask here.**
Is there an easy way I can switch to KDE for a few days and then back again if I don't like it? Is it just a package to install? Thanks.

Best to start your own thread, and not hijack someone else's thread.

You will get better exposure for your problem.

BTW, the install is easy

```
sudo apt-get install kde-desktop
```

the uninstall, now that is something else...

---

### Post by Maheriano on 2010-04-06
> **egalvan said:**
> Best to start your own thread, and not hijack someone else's thread.

You will get better exposure for your problem.

BTW, the install is easy

```
sudo apt-get install kde-desktop
```

the uninstall, now that is something else...

Okay, thanks, carry on.

---

