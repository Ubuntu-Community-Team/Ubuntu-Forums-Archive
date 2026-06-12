---
title: "Need to mount windows folder to ~/Music"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-22
Basically, I am using my Windows 7 partition for all media files. I am using Ubuntu Karmic mostly for programming so I'll often download files and play them, but I want them to reside on the Windows 7 partition.


How can I link ~/Music (and any other folder at that) to my windows partion's folder.... Basically:

/home/user1/Music  -> C:\Users\user1\My Music


Right now I am able to mount the windows partition ONLY if I click the link and enter the root pwd. This isn't exactly convenient. What I need is a pain-free way to be able to save all of my media files (music/torrents) to the windows partiation and also play them from there from Linux.

---

### Post by linuxman94 on 2010-03-22
You can use fstab, ubuntu's list of drives to be mounted on startup.

Open a teminal and type:

```
gksudo gedit /etc/fsab
```

At the bottom of the file add this line (change path to make it relevant to your configuration).

```
/path/to/folder /home/user1/Music ntfs-3g user,defaults 0 0 
```

Make sure the music folder is empty first.

Save and close the file. Reboot and the drive should be mounted.

---

### Post by TurnOfTide on 2010-03-22
Is it alright if fsab is already empty....?

edit: nvm, "fstab" found

---

### Post by patchwork on 2010-03-22
Typo...it's supposed to be fstab

---

### Post by TurnOfTide on 2010-03-22
This appears to be how to mount a partition to folder... I need to mount a folder in that partation to a directory in linux....

---

### Post by Tu1J4kXk8NUhMz on 2010-03-22
I know in OS X, it's okay if fstab is empty, as the OS uses other methods to mount drives. That's UNIX based, though, so I'm not 100% sure it will be the same with Ubuntu.

The one thing I dislike about editing fstab is the way it mounts. Essentially, you lose the ability to dynamically mount and unmount (outside of using the terminal of course). Try opening up the Software Center and typing in pysdm. The Storage Device Manager allows you essentially the same options that fstab offers, but with a bit more ease. You can mount at startup and if, for whatever reason, you need to unmount and/or remount the partition you can with the eject button in Nautilus.

---

### Post by srs5694 on 2010-03-22
If you've already mounted the partition, or if you create an /etc/fstab entry to mount it at some arbitrary point (say, /other/Windows), then you can create a symbolic link to do the job:

```

mv ~/Music ~/Orig-Music
ln -s /other/Windows/Users/user1/My\ Music ~/Music

```

These two commands move the existing ~/Music directory (you could delete it instead), then create a symbolic link to take its place. The symbolic link essentially redirects accesses to anything in ~/Music to /other/Windows/Users/user1/My\ Music. (The backslash ("\") serves as a way to tell command line to treat the following space as part of the filename rather than as a separator of two elements.)

---

