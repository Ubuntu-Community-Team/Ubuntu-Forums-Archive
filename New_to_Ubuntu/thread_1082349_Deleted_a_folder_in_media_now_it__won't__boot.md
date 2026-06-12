---
title: "Deleted a folder in media now it  won't  boot"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by BillyHunt on 2009-02-27
Oh dear my Total Noobness just caught up with me!

I've been bumbling my way around Ubuntu for a while.
I really don't know what I'm doing but I like having a dabble and I get by, just!

I recently added a spare hard drive and in doing so ended up with a redundant folder left over in media that was originally supposed to have been mounted to the new hard drive.
Inside looked like a image of the file system, when I right clicked and tried to delete it, it said I didn't have permission.
So I entered the command sudo rm -rf /media/spare 

Immediately nautilus stopped working infact nothing worked :( 
So I tried to reboot but it won't boot up

Is there any chance of getting it back?
I've booted with a live cd of 8.10 (I was using 7.10) I was just about to start to recover a few files to the spare drive but it won't let me copy and paste anything.
I don't seem to have deleted the whole operating system so that must a bonus LOL!

Help!

---

### Post by WatchingThePain on 2009-02-27
Sounds like you need an expert and if there's one expert in this forum.. I hope they get here soon.

Just a thought..does your installation media have a rescue option?.

---

### Post by BillyHunt on 2009-02-27
I'm just in the process of backing up a few things ready for the inevitable reinstall.
It might be a good time to install 8.10 while I'm at it.

It took me so long to get everything the way I wanted that I'd always avoided upgrading.

I'll have a look at the recovery options when I've done backing up.
The problem is my USB keyboard doesn't work on boot so I'll have to dig out another keyboard

---

### Post by miegiel on 2009-02-27
> **BillyHunt said:**
> The problem is my USB keyboard doesn't work on boot so I'll have to dig out another keyboard

Try the usb to ps2 adapter that probably came with your keyboard.

On data recovery : [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by geirha on 2009-02-27
Oh dear. Sounds like you mounted your root partition on /media/spare instead of the spare drive. You can mount a partition several times you see... If that was the case, it's almost the same as running that command on / instead of /media/spare, which, if you read the «Announcement: ATTENTION ALL USERS: Malicious Commands» post, is very bad. Your attempt at reboot is likely what stopped it from removing everything.

Is your /home at a separate partition? If so your home folder should be intact ...

Undeletion on ext3 filesystems (which is the default filesystem on Ubuntu) is unfortunately not possible, but the data in the files are likely still on the disk, and software like photorec and foremost can find many of them based on patterns, so photos, word/oowriter documents, audio files etc., should be salvagable since they have identifiable patterns. Their filenames are lost though, so you'll need to rename them manually.

---

### Post by BillyHunt on 2009-02-27
> **geirha said:**
> Oh dear. Sounds like you mounted your root partition on /media/spare instead of the spare drive. You can mount a partition several times you see... If that was the case, it's almost the same as running that command on / instead of /media/spare, which, if you read the «Announcement: ATTENTION ALL USERS: Malicious Commands» post, is very bad. Your attempt at reboot is likely what stopped it from removing everything.

Is your /home at a separate partition? If so your home folder should be intact ...

Undeletion on ext3 filesystems (which is the default filesystem on Ubuntu) is unfortunately not possible, but the data in the files are likely still on the disk, and software like photorec and foremost can find many of them based on patterns, so photos, word/oowriter documents, audio files etc., should be salvagable since they have identifiable patterns. Their filenames are lost though, so you'll need to rename them manually.

That does sound like what I've done doh!

The odd thing is it looks like everything is still on the drive.
Except media/spare and it's contents
Luckily my Home folder is intact, I don't recall putting it on a separate partition but I may have.

I've copied everything over to the spare drive now so nothings lost, except all the work I did getting everything running how I wanted it. 

I'm itching to start a new installation now.
But I think I'll leave it till the morning. :)

Thanks

---

### Post by geirha on 2009-02-27
That's good to hear :)

I recommend you copy /etc, but do the files back after the reinstall. Rather use it as a comparison. If you changed any files there, doing it again manually might refresh your memory of what other things you did when you set up that application.

Another thing to do is either copy the archives stored in /var/cache/apt/archives, or make a list of them ```
ls /var/cache/apt/archives >/path/to/spare/disk/installed-apps.list
```

When you install a package from the repositories, it is first stored in /var/cache/apt/archives, then installed. The package file does not get removed from there if you uninstall the package later though, but it should give you a rough overview of what packages you had installed earlier. Also, the command "sudo apt-get clean" removes all downloaded packages in /var/cache/apt/archives, so if you have run that command at some point, the package list will not be complete (handy command to know if you're low on space though).

---

### Post by BillyHunt on 2009-02-28
> **geirha said:**
> That's good to hear :)

I recommend you copy /etc, but do the files back after the reinstall. Rather use it as a comparison. If you changed any files there, doing it again manually might refresh your memory of what other things you did when you set up that application.

Another thing to do is either copy the archives stored in /var/cache/apt/archives, or make a list of them ```
ls /var/cache/apt/archives >/path/to/spare/disk/installed-apps.list
```

When you install a package from the repositories, it is first stored in /var/cache/apt/archives, then installed. The package file does not get removed from there if you uninstall the package later though, but it should give you a rough overview of what packages you had installed earlier. Also, the command "sudo apt-get clean" removes all downloaded packages in /var/cache/apt/archives, so if you have run that command at some point, the package list will not be complete (handy command to know if you're low on space though).

That sounds like a good idea
Thanks!

---

### Post by geirha on 2009-02-28
> **geirha said:**
> 
I recommend you copy /etc, but do the files back after the reinstall. 
Oops, I meant « ..., but do not copy the files back after the reinstall.»

---

### Post by BillyHunt on 2009-02-28
> **geirha said:**
> Oops, I meant « ..., but do not copy the files back after the reinstall.»

I understood what you meant ;)

I've now installed 8.10 
So far I've found it a lot more Noob friendly :)
I'm going through the process of configuring everything now, I just need to make sure I mount my spare drive correctly :D
I'm reading the documentation this time.

---

