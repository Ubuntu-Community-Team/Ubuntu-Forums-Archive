---
title: "Help on Ubuntu 8.04 update crash..."
date: 2009-01-07
forum: New to Ubuntu
---

### Post by psychicpotato on 2009-01-07
Dear experts,

I've recently been trying to update my Ubuntu 7.10 to 8.04 via Update manager.

I've downloaded the packages with no problem, but while I was installing them I stupidly pressed ctrl-alt-backspace and restarted the system. 

Now everytime I log into Ubuntu, nothing shows up except for the cursor...have I corrupted the entire update process? Is there anyway of reversing it?

Thank you very much for providing a solution to my stupidity...

Albert

---

### Post by Temposs on 2009-01-07
As far as I know, you have probably corrupted the filesystem rather badly, maybe irreversibly. 

Wait for a couple others to confirm my diagnosis, but I think the best thing for you to do at this point is to make a Live CD with Ubuntu 8.04(or 8.10) on it, boot using the Live CD, backup your important files on your Ubuntu install, and then install Ubuntu from scratch using the Live CD

---

### Post by whoop on 2009-01-07
I can imagine you still got grub up and running. Can you get into recovery mode? By a cursor do you mean you can actually enter a shell environment or do you just see a blinking cursor on an empty screen?

---

### Post by Temposs on 2009-01-07
> **whoop said:**
> I can imagine you still got grub up and running. Can you get into recovery mode? By a cursor do you mean you can actually enter a shell environment or do you just see a blinking cursor on an empty screen?

Recovery mode! That's why I said to wait for a second opinion :-)

---

### Post by psychicpotato on 2009-01-07
Thanks guys for the prompt reply!

Once I login with my username and password I get a blank background, and my cursor. I'm not sure what you mean by a shell environment...but there's absolutely nothing on the screen (no deskbars etc...)

I could get into recovery mode though.

---

### Post by whoop on 2009-01-07
Try if you can see any error message when starting your desktop from the recovery console (startx)
If that doesn't work I would try and see if you could resume/restart/continue your upgrade from the recovery console. This would be in the same manner as you upgrade a server platform.

---

### Post by Temposs on 2009-01-07
> **whoop said:**
> Try if you can see any error message when starting your desktop from the recovery console (startx)
If that doesn't work I would try and see if you could resume/restart/continue your upgrade from the recovery console. This would be in the same manner as you upgrade a server platform.

To upgrade from the recovery console, you might try something like this:

```
sudo apt-get update
sudo apt-get upgrade
```


If it can get through that, then you just might end up with a working system at the end, or you might have just a couple broken packages, which can then be repaired, probably.

---

### Post by -kg- on 2009-01-07
> **psychicpotato said:**
> Thanks guys for the prompt reply!

Once I login with my username and password I get a blank background, and my cursor. I'm not sure what you mean by a shell environment...but there's absolutely nothing on the screen (no deskbars etc...)

I could get into recovery mode though.

What I think he was asking by "Shell Environment" is the command line and nothing else.  Could you type any letters at the cursor?  If you could type something, then you were on the Command line, with no desktop GUI loaded (like the old DOS days when there was no Windows).

But if you can get it going with recovery mode, then the point will be moot.

---

### Post by psychicpotato on 2009-01-08
Dear all,

Thanks again for the help.

I've ran sudo apt-get update/upgrade on the recovery mode, but to no avail...whenever I restart I still get the same problem and cannot go further than the login screen.

I guess it's time to just re-install ubuntu on that partition...but there are certain files that I'd like to preserve though. Is there anyway of retrieving them and putting them on my other partition (Windows XP)?

Thanks!!

---

### Post by caljohnsmith on 2009-01-08
> **psychicpotato said:**
> Dear all,

Thanks again for the help.

I've ran sudo apt-get update/upgrade on the recovery mode, but to no avail...whenever I restart I still get the same problem and cannot go further than the login screen.

I guess it's time to just re-install ubuntu on that partition...but there are certain files that I'd like to preserve though. Is there anyway of retrieving them and putting them on my other partition (Windows XP)?

Thanks!!
If you can boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
That will show all your partitions; from the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
gksudo nautilus /mnt &
```
And you should be able to access your Ubuntu files. Let us know how it goes or if you run into problems.

---

### Post by whoop on 2009-01-08
You could also try doing a dist-upgrade. Especially if your /apt/get/sources.list is updated to collect from intrepid repositories.

---

### Post by whoop on 2009-01-08
You could also try doing a dist-upgrade. Especially if your /apt/get/sources.list is updated to collect from intrepid repositories.

---

### Post by whoop on 2009-01-08
You could also try doing a dist-upgrade. Especially if your /apt/get/sources.list is updated to collect from intrepid repositories.

---

### Post by whoop on 2009-01-08
If you are not willing to give up just yet you could also try doing a dist-upgrade. Especially if your /apt/get/sources.list is updated to collect from intrepid repositories.

For copying your files: there are various windows programs available for reading linux partitions (like explore2fs)

---

### Post by whoop on 2009-01-08
If you are not willing to give up just yet you could also try doing a dist-upgrade. Especially if your /apt/get/sources.list is updated to collect from intrepid repositories.

For copying your files: there are various windows programs available for reading linux partitions (like explore2fs)

---

### Post by whoop on 2009-01-08
If you are not willing to give up just yet you could also try doing a dist-upgrade. Especially if your /apt/get/sources.list is updated to collect from intrepid repositories.

For copying your files: there are various windows programs available for reading linux partitions (like explore2fs)

---

### Post by whoop on 2009-01-08
If you are not willing to give up just yet you could also try doing a dist-upgrade. Especially if your /apt/get/sources.list is updated to collect from intrepid repositories.

For copying your files: there are various windows programs available for reading linux partitions (like explore2fs)

---

