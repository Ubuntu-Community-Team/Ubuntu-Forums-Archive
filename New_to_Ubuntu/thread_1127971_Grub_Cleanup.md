---
title: "Grub Cleanup"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by kkritsilas on 2009-04-17
Hi,

I have finally installed and gotten to work correctly, Ubuntu 8.04 (Hardy Heron). I am still pretty new to Ubuntu, but like what I have seen so far; it is quite a bit faster than Vista (hardware is a Dell XPS M170 laptop/2GB Ram/250GB HD/nVidia 6800 Ultra), and I have been able to get the wireless networks, the printer, and the Video Effects working at the Extra level.

What I would like to do now is to clean up the Grub screen that allows the dual boot between Vista and Ubuntu. I think that all I need to do is to edit the menu.lst file, but I don't want to do that until I know for sure that this will not mess everything up. I have looked at the menu.lst file, and believe I understand what the commands are, and all I really want to do is to rearrange them. I currently have the Ubuntu boot lines at at the top, and so it boots, by default, into Ubuntu. I want it to default to booting into Vista, so I believe it is just a matter of bringing the 3 lines that boot Vista before the lines that boot Ubunutu. Is this correct? I also have extra lines for Ubuntu, which were created when I did my initial update after installation. I should be able to comment these lines out, or just delete them, correct? Lastly, there is a 10 second delay before Ubuntu automatically boots, and I'd like to change that to 15 or 20 seconds, that is just a value change, in the line that says timeout. Is that right?

Kostas

---

### Post by kpkeerthi on 2009-04-17
It is perfectly safe to remove old and unused kernels. Here are the steps:

1. Find out the kernel you are running currently:
```
uname -r
```
and note down the version number.

2. Open Synaptic (from System -> Administration menu) and search for **linux-image**
A green box on the left indicates that the package is installed. You might want to sort on the first column to see all packages marked green.

3. Right-click on those kernels you no longer need and select 'Mark for complete removal' (leave the kernel you found in Step 1 unselected)

4. Click Apply

All your old/unused kernels should be gone and GRUB will also be automatically updated.

Reboot and verify your GRUB. 

You can now proceed with my instructions below. 
> 
I want it to default to booting into Vista, so I believe it is just a matter of bringing the 3 lines that boot Vista before the lines that boot Ubunutu. Is this correct?

You can either move the Vista lines to the top. Or, look for the line that reads 'default 0'. That says which GRUB boot-entry (the kernel line) will be booted by default. 0 indicates first entry, 1 indicates second and so on. 
If Vista is listed as the fourth item, you would change it to **default 3**

> 
Lastly, there is a 10 second delay before Ubuntu automatically boots, and I'd like to change that to 15 or 20 seconds, that is just a value change, in the line that says timeout. Is that right?

Correct.

---

### Post by jbrown96 on 2009-04-17
What you said is correct. However, you can just change the line that says default to the number that corresponds to Vista. Note that the first entry is 0 so the third entry would actually be 2, and the line that says "Other operating sysems" (might be different) is also counted as an entry. This might be easier than changing around the order, but beware if Ubuntu installs another kernel your default may get messed up. 

you should create a backup first just in case.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
``` If it does get messed up, then just run the same command but reverse the two files.

---

### Post by NikoC on 2009-04-17
It's been a while since I have played a round with the boot options, but as far as I know, you are right on all topics:
-re-arrange lines to change boot sequence
-change time to e.g.15 or 20 to delay autoboot a bit longer

Just play safe: make a spare copy of the menu.lst file, via terminal type:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

This way you can always copy menu.lst_backup to menu.lst and have things restored as they were!

Cheers

edit: hmmz, too late, as I was typing somebody else made the same remark =)

---

### Post by Elfy on 2009-04-17
If you are going to move the whole vista stanza I would move it so it is above the automagic kernel lines

> # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

then it will always be 0

---

### Post by BrightEyesDavid on 2009-04-17
> **kpkeerthi said:**
> It is perfectly safe to remove old and unused kernels. Here are the steps:

Thanks kpkeerthi. Saved me a couple of hundred meg and makes the GRUB list look cleaner. :)

---

### Post by Paqman on 2009-04-17
> **kkritsilas said:**
> I want it to default to booting into Vista

You don't need to manually edit menu.lst. Just install the package startupmanager from  Synaptic (and get rid of any old kernels while you're there, it'll remove them from the menu.lst automatically) Startupmanager allows you to pick the default OS to boot, as well as a ton of other good stuff.

---

### Post by kpkeerthi on 2009-04-17
> **Paqman said:**
> You don't need to manually edit menu.lst. Just install the package startupmanager from  Synaptic (and **get rid of any old kernels while you're there**, it'll remove them from the menu.lst automatically) Startupmanager allows you to pick the default OS to boot, as well as a ton of other good stuff.

Can startupmanager uninstall old kernels? The last I saw was that it could only remove the kernel entries from menu.lst and not the kernels themselves. Pardon my ignorance.

---

### Post by presence1960 on 2009-04-17
> **kkritsilas said:**
> Hi,

I have finally installed and gotten to work correctly, Ubuntu 8.04 (Hardy Heron). I am still pretty new to Ubuntu, but like what I have seen so far; it is quite a bit faster than Vista (hardware is a Dell XPS M170 laptop/2GB Ram/250GB HD/nVidia 6800 Ultra), and I have been able to get the wireless networks, the printer, and the Video Effects working at the Extra level.

What I would like to do now is to clean up the Grub screen that allows the dual boot between Vista and Ubuntu. I think that all I need to do is to edit the menu.lst file, but I don't want to do that until I know for sure that this will not mess everything up. I have looked at the menu.lst file, and believe I understand what the commands are, and all I really want to do is to rearrange them. I currently have the Ubuntu boot lines at at the top, and so it boots, by default, into Ubuntu. I want it to default to booting into Vista, so I believe it is just a matter of bringing the 3 lines that boot Vista before the lines that boot Ubunutu. Is this correct? I also have extra lines for Ubuntu, which were created when I did my initial update after installation. I should be able to comment these lines out, or just delete them, correct? Lastly, there is a 10 second delay before Ubuntu automatically boots, and I'd like to change that to 15 or 20 seconds, that is just a value change, in the line that says timeout. Is that right?

Kostas

you can install startup manager. This is a GUI program that will take care of this and much more to do with GRUB. In terminal run ```
sudo apt-get install startupmanager
``` or install it in Synaptic Package Manager. To remove (actually uninstall) old kernels use Synaptic. Note: I would leave one kernel as a backup in case an update or something messes up the current kernel, that way you always have a backup.

---

### Post by Paqman on 2009-04-17
> **kpkeerthi said:**
> Can startupmanager uninstall old kernels? The last I saw was that it could only remove the kernel entries from menu.lst and not the kernels themselves. Pardon my ignorance.

No, it can't. But if you remove them through Synaptic, it'll automatically clean up menu.lst for you. 

Double-check that you're removing the right kernels in Synaptic though!

---

### Post by kkritsilas on 2009-04-22
Progress Update:

I did install Startup Manager (thanks presence1960) using the Synaptic Package manager, and used it to set Vista as default, and
also set the option to display only one kernel (I saw that it could display a variable number of kernels as a settable option). I also turned on the color option. All is well, now, except that I wanted to edit the menu.lst file, and when I tried to do the edit (using text editor), system reported that I didn't have high enough permissions. I tried to log in as root (I think that this is what the administrator's account is called), but I either forgot the password, or that isn't the proper account name. I'll leave it as is for now, but I might be in for a hard time if I decide to install Windows 7, or possibly update to Ubuntu 8.10 or the released version of Ubuntu 9.04.

Thanks to everybody for the help.

Kostas

---

### Post by barney385 on 2009-04-22
+1 for StartUp Manager

---

### Post by Paqman on 2009-04-22
> **kkritsilas said:**
> when I tried to do the edit (using text editor), system reported that I didn't have high enough permissions.

To take on enough permissions to edit files owned by root, you have to launch your text editor as root.

For example:
```

gksu gedit /path/to/file

```

---

