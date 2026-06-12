---
title: "Is there a way to do a back up of a virtual machine?"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by jlbr21 on 2009-05-19
Hi, I would like to do a clean install of my system, however, one thing I would like to keep intact is a windows xp virtual machine which I run in virtualbox 2.2.2. It's just taken me too long to configure everything and donwload much software to do a clean install of that too.

Does anybody know of a way to do a back up and then install the thing back to the way it was originally?

Thanks.

---

### Post by tuxxy on 2009-05-19
You wouldn't have to make a backup at all if you created a separate /home partition at install because this way at the new install your /home partition will not be deleted just your filesystem / 
so when you fresh install now you would be able to assign your mount points for /home and /

If you need help on creating a separate /home partition then heres [the link]("http://www.psychocats.net/ubuntu/separatehome") this guide will show you how to create a /home partition once you have installed it all to one partition, as I think you may have.

It would be easier to create one in the first place but obviously you need to save your current virtual drive.

---

### Post by jlbr21 on 2009-05-19
hi, well, i did make a separate install of my home partition when i installed ubuntu.
however, i dont get it, i mean, doesn't virtualbox and all other apps install in the filesystem? wouldn't I be wiping them out when reinstalling the filesystem?

sorry but I am a bit of a newbie at these things.

---

### Post by jlbr21 on 2009-05-19
sorry, I think I phrased that incorrectly, what I meant to say was that I did make a separate partition of home.

---

### Post by asmoore82 on 2009-05-19
many, many Linux apps store your personal config related to them in hidden files and folders in your home folder
we call these "dot-files" because their names begin with a single peroid ``.'' to hide them

So, all you have to do is preserve and handle with care your "~/.VirtualBox" folder,
which should be quite large, take mine for example:
```
**~$** du -sh .VirtualBox
11G	.VirtualBox
```

I recently upgraded from Ubuntu 8.04 LTS to 9.04 ...
the much updated VirutalBox OSE in the Repos found and migrated all of my old VBox config.

---

### Post by mgranet on 2009-05-19
Or you could just click File-->Export Appliance in VirtualBox. It will walk you right through the process of moving the VM to another place while you reinstall.

---

### Post by jlbr21 on 2009-05-19
OK, got it, now I got two ways of backing the VM up, cool!

I appreciate your help a lot.

I got another question however, when installing the new system, and after having backed up, how do I make the home folder remain the same and have the filesystem replaced?
In other words, during the installation process, at which point does the installation ask me to keep the home folder intact and the filesystem be wiped out?

Thanks again.

---

