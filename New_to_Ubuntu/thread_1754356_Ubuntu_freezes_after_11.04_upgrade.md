---
title: "Ubuntu freezes after 11.04 upgrade"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by lafona on 2011-05-09
Hi,

I have been using Ubuntu (10.10) for about six months and after upgrading to 11.04 have had the system freeze occasionally. It seems to freeze more often when I am downloading files. It freezes every time I try to download something via Steam but has also frozen while running update manager. Thanks

---

### Post by supris on 2011-05-14
a also have same problem here....on lucid lynx,i never have this problem....after installing ubuntu 11.04, my PC freeze after 10mnutes...please help mee:confused::confused::confused:

---

### Post by wariwahab on 2011-05-16
I got this problem too, system will freeze somewhere from 1 to 5 am in the morning, usually after leaving the system on for a long time. At first I thought it's the power management, or screensaver, disabling those still froze the computer.

I just tried switching to classic mode, and I got the system freeze just 30 minutes of use. I'm now trying out Classic with no effects to see if this will solve it.

It's quite frustrating, as I depend on this workstation to work 24/7. It was fine when using 10.10, and after upgrading it starts to act up. Keeping the system up to date does not help.

---

### Post by wildmanne39 on 2011-05-16
> **lafona said:**
> Hi,

I have been using Ubuntu (10.10) for about six months and after upgrading to 11.04 have had the system freeze occasionally. It seems to freeze more often when I am downloading files. It freezes every time I try to download something via Steam but has also frozen while running update manager. Thanks
Hi, do any of you have a nvidia graphics card, if so you need to use the 173 driver in additional drivers not the one marked current.:D

---

### Post by wariwahab on 2011-05-16
> **wildmanne39 said:**
> Hi, do any of you have a nvidia graphics card, if so you need to use the 173 driver in additional drivers not the one marked current.:D

Cool, will try that out, and maybe report in a few days time. What is the 173 drivers anyway? Nvidia recommends downloading the 270 one and that version is installed in Ubuntu by default. You have to go to Archived/Beta drivers section to get 173.

---

### Post by NormanFLinux on 2011-05-16
You will likely need to upgrade the kernel. The 2.6.38 kernel shipped with Natty isn't the best build.

The 2.6.39.0 kernel fixes a lot of issues and Ubuntu boots faster.

See here:

Add the kernel ppa and update your system:
 sudo add-apt-repository ppa:kernel-ppa/ppa

sudo apt-get update
 2.) Check available kernels with the command:
 apt-cache showpkg linux-headers
 kernel 2.6.39.0 should be in list.

 3.) Run the command to install kernel 2.6.39.0:
 sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

Reboot the computer after installation in the terminal is finished.

It should fix the freeze issue caused by a conflict between Broadcom wireless driver and the Ubuntu Natty default kernel panicking every time the computer connects to a wireless network.

---

### Post by wariwahab on 2011-05-16
The nVidia 173 drivers failed to load on my system, and I have to revert back to 270. I'm going to do the 2.6.29 kernel upgrade as suggested by Norman. However, I do not have Broadcom hardware on my system (it's a wired desktop), but there's no problem giving it a shot. On a related note, my AsusOne netbook which does have a Broadcom wireless (or is it madwifi), does not freeze at all.

---

### Post by wariwahab on 2011-05-16
So, my system has frozen again at around 1 am just now, so here's what I've done:

1. Uninstall nvidia drivers, and load 173. (not compatible)
2. Used the opens source drivers (does not properly support dual monitor setups :(
3. Disabled accelerated graphics (froze faster than I can say 'wha?')
4. Upgraded to kernel 2.6.39.0 (System freezes at the moment, can access it remotely)

I'm all out of options other than to downgrade the distro. Anyone done it successfully before?

---

### Post by wildmanne39 on 2011-05-16
> **wariwahab said:**
> So, my system has frozen again at around 1 am just now, so here's what I've done:

1. Uninstall nvidia drivers, and load 173. (not compatible)
2. Used the opens source drivers (does not properly support dual monitor setups :(
3. Disabled accelerated graphics (froze faster than I can say 'wha?')
4. Upgraded to kernel 2.6.39.0 (System freezes at the moment, can access it remotely)

I'm all out of options other than to downgrade the distro. Anyone done it successfully before?
Hi, mine was just a simple matter of activating the 173 driver but sense you have tried so many things that did not work, when you install and uninstall all those drivers and such it leaves behind config files and such that may be interacting badly together. I think you should try to get rid of all the old files by 
putting in a terminal
sudo apt-get --purge remove --force {name of package or driver }):P

---

### Post by wildmanne39 on 2011-05-16
> **lafona said:**
> Hi,

I have been using Ubuntu (10.10) for about six months and after upgrading to 11.04 have had the system freeze occasionally. It seems to freeze more often when I am downloading files. It freezes every time I try to download something via Steam but has also frozen while running update manager. Thanks
HI, one other thing I noticed you said you upgraded that you did not do a fresh install, I had trouble like that also, finally I did a fresh install, then I had to activate the 173 driver, but also check the bug report because different nvidia cards need different drivers to make it work in unity.

---

