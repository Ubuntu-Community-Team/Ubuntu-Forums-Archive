---
title: "Sharing /home partition between ubuntu installs"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by TripitakaUK on 2009-02-15
I have been using Hardy for a little while now and have it set up with the /home partition on a separate partition. I have just installed Kubuntu in a spare partition and want to use the /home partition between the two. Example:

sda1 - Hardy
sda2 - Kubuntu
sda3 - /home

Any idea how I can do it? I have searched on here but no joy.

---

### Post by supersonicdarky on 2009-02-15
Mount the partition as /home in fstab of kubuntu. Although it would be better if you did so during installation.

But, why install kubuntu in the first place? Just install the 'kubuntu-desktop' package in ubuntu and select the session at the login screen.

---

### Post by jimreynold2nd on 2009-02-15
If you haven't installed kubuntu yet, you can just tell it to mount sda3 to /home in "Custom partitioning" step of installation.
Or you can mount your sda3 to /home in fstab. Im assuming ext3.

/dev/sda3	/home        	ext3     	defaults       	1 	2

---

### Post by TripitakaUK on 2009-02-15
I like the idea of post #2 - didn't know I could do that.

"sudo apt-get install kubuntu-desktop" I assume?

---

### Post by supersonicdarky on 2009-02-16
Correct you are.

---

### Post by egalvan on 2009-02-16
> **supersonicdarky said:**
> 

But, why install kubuntu in the first place? Just install the 'kubuntu-desktop' package in ubuntu and select the session at the login screen.

One reason to install KDE separately is to keep KDE and Gnome separate.

Installing Gnome then KDE  works well, and I have it on all my Ubuntu installs (along with XFCE on one or two).
It lets you choose what you want or need to run, be they Gnome or KDE apps.
But it DOES clutter the menus.

Pure Gnome and pure KDE are easy with separate installs.

Just one more choice for users, in keeping with the FOSS/OSS/Linux philosophies of CHOICE!

---

