---
title: "How do I set-up a second experimental install"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by TuxImpersonator on 2009-04-24
Hey guys,
I've got a fairly stable set-up on my computer at the moment running ubuntu, but I'd like to install a fresh copy of ubuntu on a second hard drive to play around with (and most probably break many times).

How do I go about dual-booting this so that there's little to no chance of the second install being able to affect the first? At the moment I'm physically switching SATA cables!

Is there a way to alter my primary hard-drive's GRUB to have an entry for the second hard drive's ubuntu without updates/tweaks on that install playing with the main GRUB?

Any help would be much appreciated,
Thanks

---

### Post by mbzn on 2009-04-24
If you dont want to mess things up on your first install, i think your best bet is to make the second on a Virtual Machine, this will cost some performance on the second install but i believe it is good enough to play with.

---

### Post by TuxImpersonator on 2009-04-24
That sounds like a good idea mbzn, how would I go about setting that up using open software?

---

### Post by kpkeerthi on 2009-04-24
Try VirtualBox

Download the [latest deb]("http://www.virtualbox.org/wiki/Linux_Downloads") file from virtualbox's website and follow the instructions [here]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html")

---

### Post by Didius Falco on 2009-04-24
Tux,

I've nothing against using a virtual machine if you're more comfortable with that.

That said, I'm currently running 2 installs of 8.10 and an install of 9.04 with no problems. My first 8.10 install has a separate Home partition, and the other two installs don't touch it.

I installed the 2nd 8.10 in order to play around with making my own Live CD with the tools I wanted on it - primarily Gparted and Partimage, so I could work with, back up and restore partitions from a Ubuntu environment.

Speaking of which, you should consider backing up your partition(s) in any case. Knowing you can restore it makes experimenting easier, since you know you can restore it at any time you need to.

anyway, that's another option for you. Have fun!!

---

### Post by Paddy Landau on 2009-04-24
> **Didius Falco said:**
> ... play around with making my own Live CD with the tools I wanted on it - primarily Gparted and Partimage, so I could work with, back up and restore partitions from a Ubuntu environment.
Are you aware that [System Rescue CD]("http://www.sysresccd.org/") already has that set up, ready to use? I back up and restore my partitions using it.

---

### Post by longtom on 2009-04-24
> **TuxImpersonator said:**
> That sounds like a good idea mbzn, how would I go about setting that up using open software?

Google for "VirtualBox" and you will find....

However, switching cables is certainly not what you want to do for a long time.  You'll probably start damaging connectors after a while.

A dual boot is really not a big deal.  There are wonderful tutorials out here, who will help you.

- [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
- [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty) (this was the one which introduced me to dualbootin)

Pay particular attention to the partitioning.

But before you do all that ** make a backup of all your data you'll hate to loose**.
You can also make a mirror of your harddrive.

Have fun and success

---

### Post by TuxImpersonator on 2009-04-24
I think since VM is the most geeky and slighty overkill method that I have to give it a go!

One question: My wifi-ubuntu mix is currently dodgy at best, does VirtualBox route my wifi *connection* through to the vitual machine or does the VM talk *directly* to the wifi dongle, avoiding the "a leaf has fallen outside - connect lost" current connection?

---

### Post by Didius Falco on 2009-04-24
> **Paddy Landau said:**
> Are you aware that [System Rescue CD]("http://www.sysresccd.org/") already has that set up, ready to use? I back up and restore my partitions using it.

Yes, I even have a copy of it that I've used. I just got interested in customizing my own Live CD and liked the idea of being able to back up my partitions from the Ubuntu desktop.

The System Rescue CD worked, but I had to use a really crappy Vesa mode.

Thanks for taking the time to point it out, though - someone else pointing it out was how I found out about it in the first place.

---

