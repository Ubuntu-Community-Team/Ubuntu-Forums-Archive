---
title: "old laptop with hardy"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by DarinB on 2010-08-17
i have an old laptop that is barely running hardy it has 256mb ram
but it does run as a backup 
can i add fluxbox to it and dual boot it with our losing hardy?
I think putting a lighter os on it will make it work better as a back up.
and can i run thunderbird in fluxbox. I use it mainly for backup email. 
thanks

---

### Post by Ozymandias_117 on 2010-08-17
> **DarinB said:**
> i have an old laptop that is barely running hardy it has 256mb ram
but it does run as a backup 
can i add fluxbox to it and dual boot it with our losing hardy?
I think putting a lighter os on it will make it work better as a back up.
and can i run thunderbird in fluxbox. I use it mainly for backup email. 
thanks

Yeah, you can dual boot it without losing hardy. If you're going to use *buntu though, download the minimalist CD and only install things you need, to help with speed.

---

### Post by t0p on 2010-08-17
> **DarinB said:**
> i have an old laptop that is barely running hardy it has 256mb ram
but it does run as a backup 
can i add fluxbox to it and dual boot it with our losing hardy?
I think putting a lighter os on it will make it work better as a back up.
and can i run thunderbird in fluxbox. I use it mainly for backup email. 
thanks

According to a quick google, fluxbox is a window manager, not an operating system.  So if you install fluxbox, it won't be a dual-boot, as that refers to when you have more than one OS on your computer.

If my spider-sense isn't messing up, I assume when you go to log into your machine with fluxbox and hardy installed, down in the bottom left is a button marked "sessions" or maybe "options".  Go there, and you should be given the option to run Hardy with fluxbox, or Hardy with its ususal window manager (probably Gnome).

---

### Post by DarinB on 2010-08-17
Maybe i need to be more specific 
i am thinking of using Linux Mint 9 fluxbox RC. 
based on the above post maybe it is an ubuntu based distro using fluxbox as the desktop environ to make it lighter.
If this is the case...my question still stands can i add this to an old laptop that is running hardy heron and only has 256 of ram. 
i would love to get puppy linux on it but i have been very unsuccessful at getting it to dual boot with anything. I can afford to mess up the laptop since it is a back up for my email and is currently running.

---

### Post by jimrz on 2010-08-17
Yes, you could dual boot Hardy and Lucid. I would give [[COLOR="Sienna"]**_Lubuntu_**[/COLOR]]("http://lubuntu.net/") 10.04 a go. It is very light weight and uses much less ram than the standard Ubuntu.

EDIT: Linux Mint 9 also has an LXDE version (similar to Lubuntu) available that also looks to be pretty speedy.

---

### Post by Ozymandias_117 on 2010-08-18
> **DarinB said:**
> Maybe i need to be more specific 
i am thinking of using Linux Mint 9 fluxbox RC. 
based on the above post maybe it is an ubuntu based distro using fluxbox as the desktop environ to make it lighter.
If this is the case...my question still stands can i add this to an old laptop that is running hardy heron and only has 256 of ram. 
i would love to get puppy linux on it but i have been very unsuccessful at getting it to dual boot with anything. I can afford to mess up the laptop since it is a back up for my email and is currently running.

As the previous poster said, yes, you can still dual-boot, even if it's a different operating system.

Fluxbox is much lighter than LXDE, so it's up to you.

---

### Post by DarinB on 2010-08-19
I tried fluxbox as a dual boot with hardy on a sony with 256 of ram and it is much slower than hardy is. 
I am thinking of using puppy linux? can i dual boot puppy with Hardy heron? I have been completely unsuccessful in the past doing this. it there a step by step instruction no how to do this.

---

### Post by mastablasta on 2010-08-19
What kind of processor do you have? Also how much free disk space you have (especially for swap)
 
Lubuntu uses about 70 - 80 MB RAM. 
 
Mint is sort of bloated for these low level computers. Mint LXDE (based on Lubuntu) is much slower and uses more ram. Although it does come with all the necessary things you need.
 
I've just put Ubuntu 10.04 on. so far it seems quite fast. we will see later. if it start to slow down too much then it iwll be replaced by Lubuntu.

---

### Post by phillw on 2010-08-19
Hi,

when Lubuntu 10.10 comes out, using the minimal install method, there will be a 'low-fat' version of the already slim system. Usual rules apply for installing development software. You can find out more about it at [Lubuntu Testing](https://wiki.ubuntu.com/Lubuntu/Testing) I have not had chance to fully update all the instructions, but you need to change > sudo apt-get install python-software-properties
sudo add-apt-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install --no-install-recommends lubuntu-desktop
sudo apt-get dist-upgrade
sudo apt-get autoclean
cd /var/cache/apt/archives
sudo rm *
to
> sudo apt-get install python-software-properties
sudo add-apt-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install --no-install-recommends lubuntu-core
sudo apt-get dist-upgrade
sudo apt-get autoclean
cd /var/cache/apt/archives
sudo rm *
Apart from that, the actual installation instructions will be the same for 10.10 as it is for 10.04 (Just that one change in package name if you want to use lubuntu-core).

Regards,

Phill.

---

### Post by DarinB on 2010-08-19
Ok I could not get any of the above to run on my old sony 18gb 256 ram laptop it has been running hardy sluggishly....i did finally wipe out the hdd and installed lucid puppy based on ubuntu lucid it is awesome. 
so far a home run

---

