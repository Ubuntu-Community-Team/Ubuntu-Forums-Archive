---
title: "Two parter- Test Disk &amp; How to remove the lock on folders"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by perlgoodies on 2011-06-03
Hi everyone-
 
I installed Ubuntu over my Win 7 installation and I tried to get it back. I used TestDisk which everyone said it worked GREAT.

Well, it ran through Pass 1 and it made over 500 folders with renamed files. That isn't very helpful in any degree. How are you supposed to know where file X is if it's been renamed and put into a folder where it doesn't say where the information was collected? Is there something I'm missing?
 
The other question:
TestDisk made lots of folders that have locks on them. I can't copy from the folder or delete anything inside (or the folder itself).  It says it is locked by root I think.  How do I remove the lock on it? Under properties there isn't much it allows me to do and I'm the only admin/user on the box.  I want to be able to delete lots of junk files because I ran out of room and right now I can't figure out how to do it.
 
Thank you!

---

### Post by sanguinoso on 2011-06-03
You can use grep to search for contents of files. To remove a lock on a file you can use ```
sudo chmod +w
```. That adds write permissions to the file as its probably read only.

---

### Post by perlgoodies on 2011-06-03
> **sanguinoso said:**
> You can use grep to search for contents of files. To remove a lock on a file you can use ```
sudo chmod +w
```. That adds write permissions to the file as its probably read only.
 
I'll try that and see how that goes.
 
I can't really search the files as most of the files I'm looking for are binary (images) or databases.  I had hundreds of Perl scripts I've written over the last 10 years for all the sites I've built and now that they are renamed it'll take months to figure out which ones are supposed to be named what.  I don't recommend testdisk to anyone.

---

### Post by robsoles on 2011-06-03
You might need to take ownership of the files, you can do so in terminal using chown;```
sudo chown -R [COLOR=Red]myusername[/COLOR]:[COLOR=Red]mygroupname[/COLOR] ~/recovery-folder
```Please don't go around 'chown'ing anything you are not absolutely positive should rightfully be yours (your recovered files are definitely yours :))

Your OS of choice doesn't entirely rely on extensions to figure out file types so if you browse the folders using something like nautilus then the pictures should stand out somewhat and you may get some pleasant surprises with your other files.

HTH.

EDIT: You mustn't use 'myusername:myusergroup', you need to user your login username and your group will either be users or a verbatim copy of your username.

---

