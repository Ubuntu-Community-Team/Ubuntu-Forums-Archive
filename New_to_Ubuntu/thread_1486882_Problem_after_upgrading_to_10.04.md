---
title: "Problem after upgrading to 10.04"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by sitdancer on 2010-05-18
Hello.

Sorry if this ends up being a double post, but my first attempt did not show up after 5 minutes or so. I also was unable to find this problem in another thread using the search option.

I started to upgrade to version 10.04 yesterday, and it worked along just fine until I left for dinner (it had 15 minutes left to go on installing the upgrades at that point). This morning when I checked back it was stuck at 10 minutes left. Not know what to do after playing around with it a bit I shut down the computer. Upon rebooting, ubuntu did not start as usual. Instead I only got the DOS-like command input, and I am not familiar with how to use this at all (only used ubuntu in the windows-like way :( ). 

Is there a way to get it back to the way I am used to? Do I need to reinstall from a CD? If so, would that mean I loose all the data on my hard drive?

---

### Post by oaridus on 2010-05-18
I guess you need to reinstall with a 10.04 CD. And as long as you have used a separate partition for /home or /data to store your data files, you don't have to loss anything.

---

### Post by pcura on 2010-05-18
another option is get a another copy of ubuntu.......copy it from Canada mirror. i got mine working in canada location. I believe some mirror sites still have bugs in their copy.

That's just my two cents though.

---

### Post by sitdancer on 2010-05-18
I downloaded the installation CD file and then I changed the boot sequence in the BIOS to start with the CD-drive and have entered the CD in the drive. It still says "boot from hd..." after that and makes me log in, but in a DOS like interface. 

I then get the command line: "felix@felix-laptop:~$" and I don't know how I can run the installation from there. Shouldn't I be able to get an  installation client?

---

### Post by drs305 on 2010-05-18
Yes, it should show the install from CD option. I would first make sure the BIOS change "took" by rechecking it. If it shows to boot first from the CD (the correct one if you have more than one), try using another bootable CD if you have one to see if the system is really trying to boot the CD first. 

As you probably know, if BIOS isn't set correctly or if the CD is not readable for some reason you would get the results you describe.

---

### Post by oldfred on 2010-05-18
Normally the last thing installed is grub & cleanup, but it looks like you are booting into the command line. Does startx take you to the full gnome windows interface.

I would run some updates just to be sure.

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop if startx does not work
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

