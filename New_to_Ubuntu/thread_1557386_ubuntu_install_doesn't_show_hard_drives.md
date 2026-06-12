---
title: "ubuntu install doesn't show hard drives"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by athenaa on 2010-08-20
Hi,

I tried to install ubuntu on a computer that already has windows7, but when it gets to the part that I should choose a partition for ubuntu, I get nothing. It's like It can't  recognize my hard drive. I've tried the same CD on another computer, and I got the hard partitions.

Has anyone had this problem? Is it some kind of setting?

Thanks,

---

### Post by phoenixflames on 2010-08-20
What kind of hard drive do you have?

---

### Post by themusicalduck on 2010-08-20
Does the computer have RAID setup on it?

Boot it up into the live CD session first. Then open a terminal (Applications > Accessories > Terminal) and type ```
sudo apt-get remove dmraid
``` or if you want search for the package in Synaptic and uninstall it from there.

Then run the installer off the desktop link and hopefully the drives should appear.

---

### Post by rosehipzero on 2010-08-20
I have the same problem with a XFX nForce 750a MoBo of mine. I've been told using "pci=nomsi" command during installation helps solve that, but i've had no luck. Whats your MoBo?

Also, i've tried atleast 6 (more or less) different Linux OS's. I've tried Mint, Ubuntu (Jaunty, Karmic and Lucid) and OpenSUSE.

---

### Post by athenaa on 2010-08-25
> **themusicalduck said:**
> Does the computer have RAID setup on it?
 
Boot it up into the live CD session first. Then open a terminal (Applications > Accessories > Terminal) and type ```
sudo apt-get remove dmraid
``` or if you want search for the package in Synaptic and uninstall it from there.
 
Then run the installer off the desktop link and hopefully the drives should appear.
 
 
Thanks,
The ```
sudo apt-get remove dmraid 
``` worked, and the ubuntu was installed, but at the end, when it was supposed to restart, it get's stuck. I know the is no problem with CD, because I used to install ubuntu on another computer. my only guess is something wrong with the raid agian.
 
and I have to run ```
sudo apt-get remove dmraid 
``` everytime I try to install ubuntu. 
 
do you have any idea what the problem is?
 
I don't know what to do. :(

---

