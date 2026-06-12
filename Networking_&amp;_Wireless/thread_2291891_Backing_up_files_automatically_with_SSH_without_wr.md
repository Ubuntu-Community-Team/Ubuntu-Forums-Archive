---
title: "Backing up files automatically with SSH without writing the password."
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by thomas41 on 2015-08-23
Hi there,

I have two computers, one of which is always on (let's call it the server). I can access the latter through two levels of SSH (hence 2 passwords). 
I am interested in synchronize some files between both computers each time the first computer turns off.
To do so, it might be interesting to use bash files. Though I have read on expect files, it might not be a good idea to mix both. 
There are a number of issues I face. Do I absolutely need to create SSH keys, or the passwords may be simply written within the bash file ? 
If I do need, how to do it on the second layer ? 
Second, would there be any good tutorial on how to handle such back up ? (and also, to tell when the synchronization should happen). 
It would be a two-way synchronization. I haven't come up with any similar stuff on the web. 

Thanks,

---

### Post by SeijiSensei on 2015-08-24
Just create keys.  They are easier to manage and more secure.  If you need to have root access on both machines, you'll need to add the keys to /root/.ssh/authorized_keys.

Use rsync for file/directory synchronization.  It uses SSH by default.

---

### Post by Lars Noodén on 2015-08-24
Definitely use keys and rsync.  

As for examples, I put a condensed description here:
[https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync)

Perhaps it can point in the right direction.  Once you get it working you can refine it by making the key(s) single purpose and possibly replacing root access with sudo+rsync, though that is harder.

---

### Post by thomas41 on 2015-08-24
Thank you for the link, I will go through it in the coming days and come back here for updates.

---

