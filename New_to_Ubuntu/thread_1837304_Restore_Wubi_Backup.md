---
title: "Restore Wubi Backup"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by zirch on 2011-09-01
I have a backup of all the files and folders in the root directory (by selecting all and copy). I don't have the root.disk copy as a backup however. Can I use these files that I have copied and replace over the existing files in the root directory as a means of restoring to the backup state?

---

### Post by sanderd17 on 2011-09-01
This is not very good.

You should reinstall the applications, but you can copy your /home directory and /etc contains general settings.

Copying your entire root directory back will probably give issues with Grub.

---

### Post by bcbc on 2011-09-01
When you say root, I assume you mean / and not /root. 

The answer would depend on how you copied your data. If you saved the attributes, ownership, symlinks etc. it would probably work. If you just copied files then probably not.

If you just did it from nautilus, then no. You'd need something like rsync with the -a option.

---

### Post by zirch on 2011-09-01
> **sanderd17 said:**
> This is not very good.

You should reinstall the applications, but you can copy your /home directory and /etc contains general settings.

Copying your entire root directory back will probably give issues with Grub.

After reinstalling the applications, will copying /home and /etc restore application settings?

---

### Post by zirch on 2011-09-01
> **bcbc said:**
> When you say root, I assume you mean / and not /root. 

The answer would depend on how you copied your data. If you saved the attributes, ownership, symlinks etc. it would probably work. If you just copied files then probably not.

If you just did it from nautilus, then no. You'd need something like rsync with the -a option.

Yes, I meant /. I did it from nautilus, since I do not know about saving attributes, etc, nor the rsync method.

---

### Post by sanderd17 on 2011-09-01
yes, if the rights are kept.

/home/youruser is normally owned by youruser, and /etc is owned by root. So /home should give no issues if you work with one user account (and contains the major part of the settings anyway) but /etc could give issues.

---

### Post by bcbc on 2011-09-01
The other thing to check is if you were displaying hidden files when you copied the data. Most of your settings are stored in .xxx files or directories and so if you didn't copy these (Ctrl-H shows hidden files in Nautilus) you'll lose these.

What I'd do is try to backup what you've got - or is the root.disk already lost? Maybe explain what your problem is to see what options you have.

---

### Post by zirch on 2011-09-01
I did display hidden files when I was copying the data.

I made a copy of root.disk as well as all the files in root directory, just in case. But now, my backup of the root.disk file is lost, so I'm left with only the collection of files which I copied.

---

### Post by bcbc on 2011-09-01
And what's the issue with the current root.disk? Did it disappear from the \ubuntu\disks directory? Have you run chkdsk and looked in the hidden \found.000 folder?

Or is there some other problem?

---

### Post by zirch on 2011-09-01
Oh, I forgot to mention that the current root.disk file was corrupted and deleted. I can't access the found.000 folder.

---

### Post by bcbc on 2011-09-01
Review this - it takes you through the steps: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

Just to make sure it's truly gone.

---

