---
title: "Looking to do fresh install, things to remember?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by VitaminBB on 2009-05-01
Im looking to wipe out this installation of ubuntu and just do a fresh install (upgrades never seem to work 100%).

What should I remember when doing this?

Originally a friend setup my home on a seperate partition, whats the benefit of that?

Is there any easy way to transfer over the essentials? like thunderbird, firefox, pidgin etc?

What else should I do before I do the fresh install?

Thanks ...

---

### Post by billgoldberg on 2009-05-01
> **VitaminBB said:**
> Im looking to wipe out this installation of ubuntu and just do a fresh install (upgrades never seem to work 100%).

What should I remember when doing this?

Originally a friend setup my home on a seperate partition, whats the benefit of that?
[B]
Is there any easy way to transfer over the essentials? like thunderbird, firefox, pidgin etc?[/B]

What else should I do before I do the fresh install?

Thanks ...

If you want to safe some config files or data from firefox or pidgin, it will be in your home folder.

Press ctrl+h to view the hidden files and copy over any data you seem fit.

--

Remember to format your new partition as EXT4 (manual in the partition bit of the install) as by default it will use the slower EXT3.

---

### Post by blazemore on 2009-05-01
If you want a seperate /home directory, by all means do. Just really think about the sizes when you're choosing them, as it's difficult to change them later.

Personally, I'd recommend one / partition formatted as ext4.

If you back up the entire /home/user directory, you can copy it back (providing the username is the same) after the install, to preserve all your files and configs.

---

### Post by presence1960 on 2009-05-01
> **blazemore said:**
> If you want a seperate /home directory, by all means do. Just really think about the sizes when you're choosing them, as it's difficult to change them later.

Personally, I'd recommend one / partition formatted as ext4.

If you back up the entire /home/user directory, you can copy it back (providing the username is the same) after the install, to preserve all your files and configs.

Most importantly BACK UP your data. If you do a clean install that is the time to review your partitioning scheme and if necessary repartition or resize partitions. I prefer a separate /home partition, but that is not necessary, something to consider though. Do you want to use ext4 or ext3 file system? I use ext  4 and thus far no problems here. For Firefox and Thunderbird just copy your profile folders located inside /home/.mozilla for firefox and /home/.mozilla-thunderbird for thunderbird. The firefox and thunderbird profile folders will have names similar to this : 09egmirjf.default. Once the install is complete you can place these back into those folders and run in terminal ```
firefox -profilemanager
``` and ```
thunderbird -profilemanager
``` When profile manager opens create a new profile by selecting the profile folders you put into the thundebird and firefox folders. Then delete the default profile and you will be good to go. Your firefox and thunderbird will be as it was before including booksmarks, settings and emails. 

P.S. you may have to start thunderbird once prior to running profilemanager. When the account setup wizard starts just click cancel. Then run profile manager command from terminal.

---

### Post by mister_pink on 2009-05-01
If you have home on a separate partition then you're all set to keep your settings etc, - no need to do any of this copying! (Although backing up is recommended). You'll have to choose manual partitioning in the installer, which I always think is the best idea anyway. Then select your current / and set it to be / in the new install, and you current /home to be /home - but make sure you don't have the format box ticked! You might also have to tell it to use the swap partition too.

---

### Post by wizard10000 on 2009-05-01
I agree with putting /home on its own partition.  If you're running a server you may also want /var on its own partition but most people don't need that.

I generally back up /etc into my home partition before blowing everything else away - I've got a systemwide crontab, apt repositories and nfs, samba, apache and mysql configurations I'd prefer not to lose.  You only have to restore a handful of files but backing up /etc as well as /home is highly recommended.

---

### Post by MontelEdwards on 2009-05-01
> **blazemore said:**
> If you want a seperate /home directory, by all means do. Just really think about the sizes when you're choosing them, as it's difficult to change them later.

Personally, I'd recommend one / partition formatted as ext4.

If you back up the entire /home/user directory, you can copy it back (providing the username is the same) after the install, to preserve all your files and configs.
Yeah, that would be messy if you run out of space for your home.

---

