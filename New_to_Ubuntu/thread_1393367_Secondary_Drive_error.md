---
title: "Secondary Drive error"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by wolf187 on 2010-01-29
I have been using Ubuntu for the past 3 months and only recently I occurred a problem, I have on my secondary IDE cable connected a DVD-RW Drive and a hard drive, this setup has been working so far until yesterday and I am unsure what I did wrong, I get the following error when I try to mount the hard drive:
Error mounting: mount exited with exit code 1: helper failed with:
Failed to write lock '/dev/sdb1': Resource temporarily unavailable
Error opening '/dev/sdb1': Resource temporarily unavailable
Failed to mount '/dev/sdb1': Resource temporarily unavailable

Only the hard drive seems to be having this problem, my DVD-RW drive works perfectly fine, I tried disconnecting the DVD-RW drive and the error is still there.
 
Thanks in advance

---

### Post by J V on 2010-01-29
go to your disk utility and see whats wrong please...

---

### Post by HarrisonNapper on 2010-01-29
Is the HDD the Master or the Slave connection? Sometimes it doesn't matter, but sometimes you have to poke around in BIOS to make it work.

Cheers.

EDIT: see the next two posts for a more sensible first step :)

---

### Post by dnairb on 2010-01-29
This may seem a silly point, but first I would check that the cables are still connected properly - power and data, to both motherboard and drive. Unplug then plug each cable to ensure.

---

### Post by audiomick on 2010-01-29
> **dnairb said:**
> This may seem a silly point, but first I would check that the cables are still connected properly - power and data, to both motherboard and drive. Unplug then plug each cable to ensure.

I second that. Always check the simple stuff first, is my hard won experience.;)

---

### Post by wolf187 on 2010-01-30
I checked the cables and they are connected fine, both the DVD Drive and Hard Drive have their jumper settings on Cable Select, this setup works perfectly fine when I use Windows XP and it used to work before on Ubuntu(I am currently using Ubuntu 9.10), I checked in Disk Utility while using the *root* user and it gives me the same error as described earlier. Before this error happened I had installed Furiusisomount and nrgiso and it's dependencies then when the error occurred I completely removed both of these packages. Please help[ as this secondary hard drive has all my music and it sucks without the music.
Thanks in advance.

---

### Post by HarrisonNapper on 2010-02-01
Did you purge the configuration files and remove all dependencies?

---

### Post by wolf187 on 2010-02-02
I am not sure how to do that, I am still new to Linux. I tried reinstalling Ubuntu but I created another partition on my Primary hard drive and my secondary drive works perfectly fine now but I need to transfer all my applications that were installed on my previous Ubuntu system on the same Primary hard drive, I found all the Debian Packages in the /var/cache/apt/archive folder but is there a way that I can get back the applications I had on the other system because I had downloaded over 500mb of packages and I don't want to waste my cap trying to download and update them all and how can I merge the partitions into 1 without affecting the Ubuntu I am using now?

Thanks in advance.

---

### Post by HarrisonNapper on 2010-02-03
In synaptic, it's the remove completely option. Open up a terminal and run "sudo apt-get autoremove" and be sure to review the packages it removes to be sure you want to remove them. To get everything from the old system, you can move the /home/<user> directory and the /etc directory. If you have the same username, there wouldn't be problems except that you've already downloaded additional packages. You can use rsync (or grsync if you want a gui) to merge them and once you've done it, make sure to sudo apt-get update and sudo apt-get upgrade (and/or just run the updater)

Cheers.

---

### Post by wolf187 on 2010-02-15
Thanks for all the help, I decided to just reinstall the OS and download all the programs and updates I had from the South African server because I have a larger local cap limit.

---

### Post by Cheezespread on 2010-02-15
> **wolf187 said:**
> Thanks for all the help, I decided to just reinstall the OS and download all the programs and updates I had from the South African server because I have a larger local cap limit.

You can always copy the deb files in the /var/cache/apt/archives and use it for your new installation. You wouldnt need to download all of them again.

PS : oops. Din see the earlier post. Sorry

---

### Post by HarrisonNapper on 2010-02-16
> **Cheezespread said:**
> You can always copy the deb files in the /var/cache/apt/archives and use it for your new installation. You wouldnt need to download all of them again.

PS : oops. Din see the earlier post. Sorry

You wouldn't need to download, but I assume that apt would need to run the install routine for all packages, correct? Would you have to fix broken packages to get it working?

---

