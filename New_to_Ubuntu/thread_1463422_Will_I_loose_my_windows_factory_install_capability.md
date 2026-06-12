---
title: "Will I loose my windows factory install capability?"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by soft-e on 2010-04-26
Hello,
 
I have a windows vista laptop and I'd like to install ubuntu as well on a different partition. My question is I have a factory install option (as with all modern laptops) and I do not want to loose that. Please let me know if I can install ubuntu and still be able to do a factory image install of my windows OS if I have to? 
 
Thanks,
soft-e

---

### Post by Megaptera on 2010-04-27
Hi,
It's likely that your Windows is on 'C' and your recovery is on 'D' (using Windows terminology). You can let Ubuntu install on 'C' alongside Windows by using the defaults when you install Ubuntu. This won't touch 'D' as you probably have to press F11 or similar to access recovery at boot.
With my Dell I have the three recovery discs as well as the recovery partition (20gb approx). I therefore deleted the recovery partition and installed Ubuntu there to accomplish my dual-boot.
Don't delete the recovery partition unless you've got the recovery discs and have tested them!

Remember to backup beforehand just in case!

---

### Post by clhsharky on 2010-04-27
HI soft-e

You can do a successful install of Ubuntu and keep your vista.
BUT it will take planning, backup, preparing, the right howto guide, and some help from forum. If you throw the Ubuntu cd in and click install, you will regret that your original plans will not come true.
As for now listen to the advise you get, and try to understand whats going to happen, don't jump in to fast, its not real hard with the right tools and help. We will get you there, OK.

Have you used WUBI to install Ubuntu inside window? Its a good way to learn Ubuntu, and it can be uninstalled. 

I'll get back to you, let us know more.

Sharky

---

### Post by 3rdalbum on 2010-04-27
You'll be able to use the recovery partition after installing Ubuntu, just make sure that you don't format the recovery partition.

---

### Post by miyagison on 2010-04-27
> **3rdalbum said:**
> You'll be able to use the recovery partition after installing Ubuntu, just make sure that you don't format the recovery partition.

In addition; if you do have the original factory restore disk then you are safe as in most cases this disk will also re-create the recovery partition. If you have a mainstream laptop such as Gateway, Dell, HP/Compaq then I think you can just send in a request for a restore CD/DVD and in most cases you don't need to pay for them as they are computer/hardware specific.

:guitar:

---

### Post by lisati on 2010-04-27
> **miyagison said:**
> In addition; if you do have the original factory restore disk then you are safe as in most cases this disk will also re-create the recovery partition. If you have a mainstream laptop such as Gateway, Dell, HP/Compaq then I think you can just send in a request for a restore CD/DVD and in most cases you don't need to pay for them as they are computer/hardware specific.

:guitar:

As well, some computers come with software that let you prepare a set of recovery disks from the recovery partition.

---

### Post by Dalek Draco ON LINUX on 2010-04-27
> **soft-e said:**
> Hello,
 
I have a windows vista laptop and I'd like to install ubuntu as well on a different partition. My question is I have a factory install option (as with all modern laptops) and I do not want to loose that. Please let me know if I can install ubuntu and still be able to do a factory image install of my windows OS if I have to? 
 
Thanks,
soft-e

Usually the D drive has the factory image saved there so that if the C drive fails or has malware, you use the D to recover. To check boot into windows and select the D drive, you should find a folder that has the recovery files in it. If so you want to make sure when you partition the harddrive to install ubuntu, that you don't overwrite the D drive.

---

### Post by Mark Phelps on 2010-04-28
> **soft-e said:**
> Hello,
 
I have a windows vista laptop and I'd like to install ubuntu as well on a different partition...

In that case, use the Vista Disk Management utility to shrink your Vista OS partition and boot into it afterward to ensure it still works.

Then, install Ubuntu into the free space.  It will overwrite your MBR as a byproduct of the installation, so when you next boot, you will boot directly into Ubuntu.  Once in Ubuntu, open a terminal and enter "sudo update-grub".  That should add the entries needed to your GRUB config file.

The next boot should present you with an OS selection menu.

BTW, if you have a restore CD, not a DVD, I wouldn't presume that it is all you would need to restore your Vista install.  More likely, the restore CD only contains WinPE, and when you boot, it looks for the restore image on your drive.  So, I would make sure you do not overwrite or erase the restore partition.

---

