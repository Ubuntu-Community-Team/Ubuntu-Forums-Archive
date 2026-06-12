---
title: "What command would I use to return data from a Rsync backup?"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by mikodo on 2010-04-07
Hello everyone,

I am following from Ubuntu Documentation on rsync, for a Local Backup from my computer to an external HD. The guide suggests:

sudo rsync -azvv /home/path/folder1/ /home/path/folder2

So, to use command to backup data to my external HD I will use this:

sudo rsync -azvv /home/mikodo/ /media/6c12ee63-f305-484d-80d0-9f413e799fc0/

To return data to my computer, I doubt reversing the command like below would be wise, as it would change the permissions to root, wouldn't it? 

 rsync -azvv /media/6c12ee63-f305-484d-80d0-9f413e799fc0/ /home/mikodo/

So, what command would I use in Terminal, to restore the backup data? It doesn't say in the guide.

Thank you.

---

### Post by Paqman on 2010-04-07
> **mikodo said:**
> 
To return data to my computer, I doubt reversing the command like below would be wise, as it would change the permissions to root, wouldn't it? 


Nope. The switch -a is archive mode, which preserves owners and groups.

---

### Post by mikodo on 2010-04-07
> **Paqman said:**
> Nope. The switch -a is archive mode, which preserves owners and groups.
Thank you for the reply. So, to be sure, just running the reverse of the code would return data to my computer. Nothing else would have to be run?

Thank you.

---

### Post by Paqman on 2010-04-07
> **mikodo said:**
> Thank you for the reply. So, to be sure, just running the reverse of the code would return data to my computer. Nothing else would have to be run?


Yep. It's always a good idea to run a test with some junk (or duplicate) data before you unleash a backup regime on your real data, if only for peace of mind.

You might want to take a look at anacron for automating your backups, too. It's really simple to use.

---

### Post by mikodo on 2010-04-07
> **Paqman said:**
> Yep. It's always a good idea to run a test with some junk (or duplicate) data before you unleash a backup regime on your real data, if only for peace of mind.

You might want to take a look at anacron for automating your backups, too. It's really simple to use.

Thanks for the replies. I will follow your advice, and look again at anacron.

Mike

---

