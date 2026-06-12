---
title: "No complete boot, after a messy shutdown"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Ubermeister on 2011-05-01
Hi!  Running Pinguy 10.10.1 X86 on my laptop, it is the only OS installed.

After messing with updates, wich took a long time, i decided to reboot, in the middle of the update.

Now, when booting, i choose the normal login, but i only get to a non graphic mode (looks like dos) 

It works perfect in fail-safe mode, and if i choose to log in with the earlier version.

Would reinstalling Grub fix this maybe?

look at the pictures.

I am hungover, newbie and Swedish..

---

### Post by pinballwizard on 2011-05-01
> **Ubermeister said:**
> 

It works perfect in fail-safe mode, and if i choose to log in with the earlier version.



Boot the "earlier version" that works, and let the update complete this time?

---

### Post by Ubermeister on 2011-05-01
I have logged in on "the earlier"  (the highlighted in the picture) and updated system, no difference.

[http://ubuntuforums.org/showthread.php?t=1698409](http://ubuntuforums.org/showthread.php?t=1698409)   Like this. Could be a lot of reasons i guess.. =)

---

### Post by oldfred on 2011-05-01
If you get the grub menu, it is not a grub issue.

From command line run the full set of updates. Normally from chroot as you cannot get to command line. Anything after a # is a comment.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: 
sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by Ubermeister on 2011-05-02
Since the install is only 2 days old and i have 2 days of Linux experience, i tthink i'll do a complete new install.

Thanks for helping me.  I'll be back with other questions when i have learned something.

---

