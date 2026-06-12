---
title: "Is there an easy program for file backup?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by btedm on 2010-01-30
I wanted to back up my /home directory.
  
I was using Unison and happily backing up the /home directory until I found that it was not backing up the hidden files such as my email.  

I tried "Simple Backup" which had a nice user interface, but the backups failed -- the CPU went to 100% but the process which was supposed to be working in the background did not show up on the System Monitor.  

I tried file-roller.  In Ubuntu 9.04 it gave up on access denied (there was no helpful information saying which file but I think it was in .wine).  In Ubuntu 9.10 which I just installed it worked for /home including .wine.  I then tried backing up /usr and received a message "an error occurred while adding files to the archive", although in a quick scan I did not find anything missing and retrieving a sample file worked.

Does anyone know of a reliable backup program with a good user interface (and good error messages if something goes wrong)?  I know I could spend some time and learn to write a script file to do the backup, and I may do this as a learning exercise.  But for such a routine task it should not be necessary for a user to resort to programming.

---

### Post by Psumi on 2010-01-30
Back in time?

---

### Post by tom.swartz07 on 2010-01-30
> **btedm said:**
> I wanted to back up my /home directory.
  
I was using Unison and happily backing up the /home directory until I found that it was not backing up the hidden files such as my email.  

I tried "Simple Backup" which had a nice user interface, but the backups failed -- the CPU went to 100% but the process which was supposed to be working in the background did not show up on the System Monitor.  

I tried file-roller.  In Ubuntu 9.04 it gave up on access denied (there was no helpful information saying which file but I think it was in .wine).  In Ubuntu 9.10 which I just installed it worked for /home including .wine.  I then tried backing up /usr and received a message "an error occurred while adding files to the archive", although in a quick scan I did not find anything missing and retrieving a sample file worked.

Does anyone know of a reliable backup program with a good user interface (and good error messages if something goes wrong)?  I know I could spend some time and learn to write a script file to do the backup, and I may do this as a learning exercise.  But for such a routine task it should not be necessary for a user to resort to programming.

I was just looking to do something like this. I found a simple script that someone posted in reply- ill share it with you:


I tweaked it a bit for my purposes, im sure you could do the same:

```
#!/bin/sh
####################################
#
# Backup to external USB drive
#
####################################

# What to backup. *EDITABLE*
backup_files="/home/tom"

# Where to backup to. *EDITABLE*
dest="/media/backup"

# Temporary storage for file as its being processed. *EDITABLE*
temp="/media/Data"

# -----DO NOT EDIT BELOW THIS LINE----- #
# Create archive filename.
#day=$(date +%a)
#time=$(date +%R)
hostname=$(hostname -s)
#archive_file="$hostname-$day-$time.tgz"
archive_file="$hostname.tgz"
# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo

# Backup the files using tar.
tar czf $temp/$archive_file $backup_files
#compress to save space.
gzip -9 $temp/$archive_file
#Remove previous file and copy new version
mv $temp/$archive_file $dest
# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
ls -lh $dest
```


Hope this helps!

---

### Post by warfacegod on 2010-01-30
I like this:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by jhigz on 2010-01-30
I would second Back in Time.

The default setting is to exclude hidden files and folders, but by using links to this data, I'm able to backup Evolution, Tomboy, or whatever, and leave the default settings as is. I simply store the links in a folder within my home and it grabs the hidden data.

---

### Post by tom.swartz07 on 2010-01-30
> **warfacegod said:**
> I like this:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

Hey warface- isnt that the same method that my script does? :popcorn:

Im just saying.. :lolflag:

---

### Post by NightwishFan on 2010-01-30
+1 more for Backintime. It seems excellent. It has Gnome and KDE frontends.

---

### Post by warfacegod on 2010-01-30
> **tom.swartz07 said:**
> Hey warface- isnt that the same method that my script does? :popcorn:

Im just saying.. :lolflag:

You don't think I actually *read* your posts do you?


It probably is but reading the thread would give the OP a better idea of what is happening, as well as a way to know what to take out of the backup that is unnecessary. ...And it's a shorter code.:P


Fixed my laptop finally.

---

### Post by falconindy on 2010-01-30
> **btedm said:**
> ...for such a routine task it should not be necessary for a user to resort to programming.
Just because something is routine doesn't mean it's simple. Backups need to be precise -- permissions, ownership, and timestamps all need to be preserved in order for the archive to be useful. Structure is important for ease of recovery, and in turn, the recovery (and backup) process needs to be simple as well.

To that extent, I've **always** written my own backup scripts, to ensure that I get exactly what I want. Call me paranoid, but I only trust my own software to handle my backups.

If you want to write your own, I highly recommend centering the script around rsync, as it's outrageously flexible and reasonably quick. I'm currently on my [3rd solution]("http://github.com/falconindy/SquashFu"), which has evolved from a simple rsync wrapper to a full blown Bash program that offers incremental backups and compression (via somewhat exotic methods).

---

### Post by perce on 2010-01-30
If you don't mind the terminal, rsync is efficient and quite easy to use

---

### Post by switch10 on 2010-01-30
I used to use back in time.  Now I just manually rsync my /home.  Using the "restore" button (I think thats what they call it) in back in time failed for me, so I had to restore manually as well.

---

### Post by btedm on 2010-01-31
Thanks everyone for your suggestions.  I tried "Back in Time" and it worked well for me.  I also restored a few files and it worked well.  I restore a few files because of a bad experience with Acronis (in Windows XP) where the backups saved without any error but the files were corrupt when they were restored.  When I have more time I will try using rsync or possibly .tar because I see there are many options which are not in Back in Time.  Thanks again all.

---

### Post by ElSlunko on 2010-01-31
Yep +1 for back in time. It's saved my butt in many occasions.

---

