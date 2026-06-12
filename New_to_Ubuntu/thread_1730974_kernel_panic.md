---
title: "kernel panic"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-16
For the second time my Ubuntu 10.4 LTS has froze up.  I first tried Ctrl+Alt+Bksp with no results.  Then I tried Ctrl+Alt+Printscreen followed in order with REISUB, with no results.  I was forced to hold down the fromt power button until it turned off some 5 seconds later.  Now, when I boot up into Linux I get this message:  [   1.004565] Kernel panic - not syncing: UFS:Unable to mount root fs on unknown - block (0,0)
 
How do I fix this problem?  Also, are threre stability problems with Ubuntu 10.4 I need to be aware of?

---

### Post by drs305 on 2011-04-16
My suggestion would be to boot the LiveCD and then do an fsck check on your unmounted Ubuntu partition. I use the following command. Change the partition if your's is not sda**5**:
```
sudo umount /dev/sda5  # Just to ensure it's not mounted.
sudo e2fsck -f -y -v /dev/sda**5**
```

---

### Post by TCMGO on 2011-04-16
Thank you for replying.  Once I run fsck, what do I look for?  I am an absolute newbie, so this crash is both overwhelming and somewhat discouraging.

---

### Post by drs305 on 2011-04-16
> **TCMGO said:**
> Thank you for replying.  Once I run fsck, what do I look for?  I am an absolute newbie, so this crash is both overwhelming and somewhat discouraging.

This command will check the partition for errors and fix them. It will generate a report but it won't mean a lot to you. You can post the results if you don't understand them and the system still won't boot.

If you are still having problems, we can take a look at the status of your boot files. Go to the following site and download and run the boot info script. Post the contents of the RESULTS.txt in a new thread so we can offer further advice.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by TCMGO on 2011-04-16
Thank you  . . . I am on it right now.

---

### Post by TCMGO on 2011-04-16
Before doing the fsck check I ran a memtest86, which initially failed. Then I pulled the two sticks of RAM, cleaned them and then tested each one individually and they passed. Then I reseated them both and tried to reboot Ubuntu and this time it came up. Question: Can funky RAM cause the kernel panic I was having and did my RAM cleaning resolve the problem? Also, do I still need to do a fsck check of the Ubuntu partition? And if this affirmative, do I still do it with the bootable LIVE CD?

---

### Post by drs305 on 2011-04-16
> **TCMGO said:**
> Before doing the fsck check I ran a memtest86, which initially failed. Then I pulled the two sticks of RAM, cleaned them and then tested each one individually and they passed. Then I reseated them both and tried to reboot Ubuntu and this time it came up. Question: Can funky RAM cause the kernel panic I was having and did my RAM cleaning resolve the problem? Also, do I still need to do a fsck check of the Ubuntu partition? And if this affirmative, do I still do it with the bootable LIVE CD?

Yes the RAM may have been the problem or resetting them may have triggered some other check which fixed things. 

If you system is booting normally I wouldn't bother with the fsck check. This check is automatically performed at preset intervals (the default is every 30 boots) so it will be checked if you haven't modified the last digit of your fstab setting. 

Happy Ubuntu-ing !

---

