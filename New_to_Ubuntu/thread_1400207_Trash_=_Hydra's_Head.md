---
title: "Trash = Hydra's Head"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by lile001 on 2010-02-06
Trash is like the multiheaded hydra - when you cut off a head, two grow back!

I'm trying to do a backup, and that is actually going rather well, EXCEPT I keep trying to not back up stuff in the trash.  Of course, since I don't know what I am doing, I have started making a backup.tgz file several times, realized several times it was trying to back up and old gigantic backup.tgz file, aborted, and now there is another backup.tgz that I don't want to back up.  I've been doing this all morning, like groundhog day. 

If I start Nautilus as root, I see a folder called /root/.local/share/Trash/files. 

This folder contains the files I tried to delete.  

Deleting it makes it come back, because this is the Trash.  OK. Lets dump the trash.

However, if I go to Trash, on the left hand column of the nautilus screen, it claims that "The Folder Contents could not be displayed.  Sorry, could not display all the contents of trash. operation not supported."  After that, the "Empty Trash" button is not active, which means I can never get rid of these files.  Grrrr. I'm root, why can't I empty my trash?  

Here is the command that I am using to back everything up.  
sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/larry/.Trash --exclude=/home/qhyrrae/.Trash --exclude=/home/.Trash-root --exclude=/home/.Trash-0 /

I don't understand what half of this gibberish means.  Is there a way I can exclude ANYTHING named Trash, wherever it is found? How about ANYTHING named backup.tgz?  Every time I think I have found all the trash, another one pops up!

---

### Post by lile001 on 2010-02-06
This command:

sudo find / -name .Trash\* -print

Is supposed to find anything named .Trash, except it doesn't find

/root/.local/share/.Trash

Grrr.  

I've added this directory to the exclude list in my backup command. 

How do I fix this tar backup command so it doesn't backup anyting named backup.tgz and anyting named TRASH?

---

### Post by mushwars on 2010-02-06
The point of backups is to back them up on a different drive. If you are backing them up on the same drive, ofc you are going to have problems, and that doesnt make any sense to back them up to the same drive, so in essence you are not really backing up anything just creating a headache.

You should not be running nautilus as root. 

Also if you need to cp or mv files use the Terminal that is what is good for you can also use sudo command to give you temporary root.

---

### Post by dearingj on 2010-02-06
> **lile001 said:**
> This command:

sudo find / -name .Trash\* -print

Is supposed to find anything named .Trash, except it doesn't find

/root/.local/share/.Trash


Be careful with those periods. In your original post you mentioned the folder /root/.local/share/Trash/files - note the lack of a period in that Trash. Perhaps you should try this find command instead?

```
sudo find / -name Trash\* -print
```

---

### Post by lile001 on 2010-02-06
*You should not be running nautilus as root. *

Sorry, I disagree.

---

### Post by lile001 on 2010-02-06
> **dearingj said:**
> Be careful with those periods. In your original post you mentioned the folder /root/.local/share/Trash/files - note the lack of a period in that Trash. Perhaps you should try this find command instead?

```
sudo find / -name Trash\* -print
```

Let's focus on the tar command.  Is there a way to exclude ANYTHING named "backup", or ANYTHING in any folder called trash?

---

### Post by lile001 on 2010-02-07
> **lile001 said:**
> Let's focus on the tar command.  Is there a way to exclude ANYTHING named "backup", or ANYTHING in any folder called trash?

Seeing no replies, I'll assume there isn't.  Here is what worked for me:  Once I had an external drive working properly (whole 'nuther thread) I cd to the external drive and create a tar file there.  Saves moving it later.  Here is the command I finally used that worked:


sudo tar cvpzf [todaysdate]backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude homebackup1.tgz --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/[user]/.Trash --exclude=/home/[user]/.Trash --exclude=/home/.Trash-root --exclude=/home/.Trash-0 --exclude=/root/.local /

It can also back up just the home folders by adding /home instead of / as the final item.

---

