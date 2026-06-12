---
title: "Question  How do I copy across existing settings from one version of 10.10 to anothe"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by RoyHobbs on 2010-12-11
Hi
Due to a problem I had with a 10.10 upgrade ([http://ubuntuforums.org/showthread.php?t=1642944](http://ubuntuforums.org/showthread.php?t=1642944)) and the need to access data on the pc I upgraded, I downloaded the live CD and installed on the same pc. Now I have two versions of 10.10 on the same pc but in different partitions. Is there any way I can copy my settings from the partition that is not working (the upgraded one) to the one that is working? I have also posted this question in the upgrades sections.  Thanks

---

### Post by chaanakya_chiraag on 2010-12-11
All user settings are stored in your home directory, usually in hidden folders (folders starting with a ".").  Not sure if that's helpful for what you are trying to do...

---

### Post by RoyHobbs on 2010-12-11
Hi
Thanks for the reply, however should I copy across all the files?

---

### Post by laidback on 2010-12-12
Use a memory stick or CD and write any files from your home directories, ~/.subdirectory, to it. Then write back to the new installation. When I've done this in the past I've renamed the existing subdirectories in the new installation *.old or something similar so that I don't actually overwrite them. It's quite a while since I did this so cannot remember all the issues.

For some applications there are export/import utilities, e.g Evolution, Firefox. You may need to install the utility first.

I think it would also be possible to copy the whole of your existing /Home directory out to CD/DVD or external HD and then copy it back to the new system.

---

### Post by Paqman on 2010-12-12
> **RoyHobbs said:**
> Hi
Thanks for the reply, however should I copy across all the files?

Yep. Just to be sure, run the following command after pasting them in, just to make sure you've got ownership of all the files:
```
sudo chown -R username:username /home/username
```

---

### Post by warfacegod on 2010-12-12
I wouldn't copy over all the settings directories at the same time. Something in one of them may be contributing to the issues you're having. It's tedious but I would do them one at a time.

---

### Post by warfacegod on 2010-12-12
By the way, you likely won't need all of the .name folders. Things like .mozilla .themes .icons and applications you have changed the preferences for.

---

### Post by matt_symes on 2010-12-12
Hi

Why not just mount the old partition directly under the new operating system? It will save you messing about with a USB stick.

While a USB stick is a good solution, in this case you may not need it.

Kind regards

---

### Post by RoyHobbs on 2010-12-14
> **matt_symes said:**
> Hi

Why not just mount the old partition directly under the new operating system? It will save you messing about with a USB stick.

While a USB stick is a good solution, in this case you may not need it.

Kind regards

Hi

Thanks for this response, however what do you mount the old under the new?  While I've been using Ubuntu for a while I'm still a bit of a newbie so any basic instructions would be greatly appreciated!;)

---

### Post by low_rider on 2010-12-14
You can mount other drives (and just about everything else) using the mount command.  The basic format would look something like this:
mount /dev/sda1 /mount

or a more generic form:
mount (device you want to mount) (place you want to mount it to)

you can find out more options by checking out the man pages (man mount).

Hope this helps!

---

### Post by RoyHobbs on 2010-12-14
> **low_rider said:**
> You can mount other drives (and just about everything else) using the mount command.  The basic format would look something like this:
mount /dev/sda1 /mount

or a more generic form:
mount (device you want to mount) (place you want to mount it to)

you can find out more options by checking out the man pages (man mount).

Hope this helps!

Thanks for the quick reply, however is there any way I can mount drives automatically when I start a new session?

---

### Post by low_rider on 2010-12-14
Yes you can edit the /etc/fstab file so that it includes your drive on startup.  You'll probably want to learn a little bit about the syntax so that you make sure you get the command right.  For instance I have my computer load my windows partition on boot so I have this line in my fstab:
/dev/sda1	/media/windows	ntfs	errors=remount-ro 0	  1

---

