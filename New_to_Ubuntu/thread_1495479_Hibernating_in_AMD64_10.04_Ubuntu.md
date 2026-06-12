---
title: "Hibernating in AMD64 10.04 Ubuntu"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Saiyaman on 2010-05-28
I've been trying to find a way to hibernate in 10.04 Ubuntu, but none of them seem to work.

I first tried the Help & Support icon in the panel, and typed in variations of "hibernate" and "enable hibernation", but all it came up with was pretty much unrelated articles except for one.  That article told me to "change the gconf key" or something.  SO, I looked up gconf, and it took a LONG time to try to sort everthing out.  To make a long story short, I ran "gconftool" to change "/apps/gnome-power-manager/lock/hibernate" to "true", with the exact terminal command: "gconftool --set /apps/gnome-power-manager/lock/hibernate = true".  Now I'm still not sure if it's the right command, because there weren't any specific commands in the Help icon, but I checked with "--set", and it returned "true", so I thought I did it.  I checked, it wasn't there; I restarted and checked, still not there; did that like two or three more times, just to make sure.  Still wasn't there. Then, I did a google search, and found an ubuntu documentation page that provided a debian package named exactly "hibernate_1.99-1.1_all.deb".  I downloaded that and gave that a try.  I restarted to find hibernate still not there, even in the power management preferences thing, and tried reinstalling to still no avail.  OK, typing all that was really tedious...anyways, could someone help me just enable the hibernate power option and get it on to the drop down power menu?

---

### Post by -humanaut- on 2010-05-28
Are you using any proprietary video cards?

---

### Post by Saiyaman on 2010-05-28
> **-humanaut- said:**
> Are you using any proprietary video cards?

Yes, I'm using an NVIDIA GeForce 8400M GS.

---

### Post by -humanaut- on 2010-05-28
Have you installed the latest Current for your card through gtk-jockey?

---

### Post by Saiyaman on 2010-05-28
> **-humanaut- said:**
> Have you installed the latest Current for your card through gtk-jockey?

What is a "Current"?  I have the latest driver (the recommended NVIDIA driver) activated/installed via hardware drivers system admin thing, if that's what you mean?

---

### Post by jerenept on 2010-05-28
> **Saiyaman said:**
> What is a "Current"?  I have the latest driver (the recommended NVIDIA driver) activated/installed via hardware drivers system admin thing, if that's what you mean?

Yes, but i am sure this is only important for suspend.. You also need to have a swap partition larger than your memory size.
How much RAM do you have, and what size swap do you have? (check Disk Utility to find out swap size)

---

### Post by gorostas on 2010-05-29
Same problem here with me, 

have x64 ubuntu 10.04 and hibernate doesn't work. 

I chacked my swap size like jerenept suggested with disk utility and I have 1.6Gb size and my pc has 3GB ram.

Ok, how do I make the swap larger ? I tried that with disk utility but seams that is not posible

Thanks for help

---

### Post by gorostas on 2010-05-29
Ok, I have found solution, for someone else if they got in some similar problem like me.

This page have solution, I have successfully grown my swap by 5gb with this tutorial of 4 steps!

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

thanks

---

### Post by Saiyaman on 2010-05-29
> **jerenept said:**
> Yes, but i am sure this is only important for suspend.. You also need to have a swap partition larger than your memory size.
How much RAM do you have, and what size swap do you have? (check Disk Utility to find out swap size)

I see... I have 4GB ram, with no swap partition.  I remember having the 10.04 install CD not set up a swap partition because I only had 45 GB free space.  I thought the OS saves the hibernating info/session onto the filesystem itself though?  I'm pretty sure that's what Windows XP/Vista does, they don't have any swap partition...

---

### Post by anewguy on 2010-05-29
> **Saiyaman said:**
> I see... I have 4GB ram, with no swap partition.  I remember having the 10.04 install CD not set up a swap partition because I only had 45 GB free space.  I thought the OS saves the hibernating info/session onto the filesystem itself though?  I'm pretty sure that's what Windows XP/Vista does, they don't have any swap partition...

The page file in Windows is the equivalent of the swap file in Linux, but in some Windows system a hibernation file is also created.  For Linux, you can have no swap, a swap file or a swap partition.  If you want to create swap, and want it be part of the file system and not a partition, you should read this link for more information on the Linux swap:

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

Dave ;)

---

### Post by anewguy on 2010-05-29
OOOPPPSSS --- dup post.  Removing text....

---

