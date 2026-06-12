---
title: "Can 9.10 and 8.04 share /home and /usr/local/bin ?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Physicist on 2009-12-05
I have a 8.04 who have /, /home, and /usr/local/bin in different primary partitions. Can I install 9.10 and use existing /home and /usr/local/bin for it ?

---

### Post by Paqman on 2009-12-05
You can share your /home partition. Just make sure you use different accounts for different systems.

---

### Post by Physicist on 2009-12-05
Why /usr/local/bin can't be used ?

Is it possible to resize /home or /usr/local/bin to free some disk space without destroying 8.04?

---

### Post by 3rag0n on 2009-12-05
/home can be shared as long as you use different accounts. If you use accounts with the same name, your presonal configuration files will conflict. As for /usr/local/bin, it ussually contains executables of installed programs, ususally executables of programs that you will compile from source and then install. So it is definitely not a good idea to share /usr/local/bin. 
Because if you DO share it, then you might find that certain programs might not work ( if you have a 32-bit OS and the other as 64-bit, or if there are certain library differences between the two OS's you MIGHT face problems with running certain programs.

About resizing, you can resize /home if it is a separate partition and has enough disk space. /usr/local/bin is usually not a separate partition, and so you can't really "resize" it. Cheers :)

---

### Post by Physicist on 2009-12-05
Thanks for the answer. I have more questions in the following

> **3rag0n said:**
> /home can be shared as long as you use different accounts. If you use accounts with the same name, your presonal configuration files will conflict.


What do you exactly mean by conflict ? What if I want to use the same configuration files for my softwares, e.g., I do want the same .emacs, etc. ?

> **3rag0n said:**
> As for /usr/local/bin, it ussually contains executables of installed programs, ususally executables of programs that you will compile from source and then install. So it is definitely not a good idea to share /usr/local/bin. 
Because if you DO share it, then you might find that certain programs might not work ( if you have a 32-bit OS and the other as 64-bit, or if there are certain library differences between the two OS's you MIGHT face problems with running certain programs.

As I said, I have /usr/local/bin in a separate primary partition.

The two OS's will be on same physical machine and are all 32-bit. Besides this reason, any other possible reason I can't share /usr/local/bin ?

> **3rag0n said:**
> 
About resizing, you can resize /home if it is a separate partition and has enough disk space. /usr/local/bin is usually not a separate partition, and so you can't really "resize" it. Cheers :)

How do I resize ?

---

### Post by 3rag0n on 2009-12-05
> What if I want to use the same configuration files for my softwares, e.g., I do want the same .emacs, etc. ?


It's your choice if you want to share it. But remember that config files of programs other than emacs will be shared. You can face problems when programs which use those config files have different versions in each OS. The config format might have changed in a newer version.
I have tried sharing a /home with the same user account and I HAVE had such problems.

> As I said, I have /usr/local/bin in a separate primary partition.

The two OS's will be on same physical machine and are all 32-bit. Besides this reason, any other possible reason I can't share /usr/local/bin ?


Not really. Go ahead, because ubuntu rarely ever writes anything to /usr/local/bin unless you explicitly do so. But whatever programs you have in that directory/partition will not run in your new OS till you install the necessary dependency libraries.

To resize, unmount that partition and click edit with it selected. Then select the new size for that partition. Click apply, the partition will be resized. The leftover size will be shown as free space.

**Take care, you can have a maximum of four primary partitions!!!**

---

### Post by Physicist on 2009-12-05
I forgot to ask, can I share /swap ?

> **Physicist said:**
> I have a 8.04 who have /, /home, and /usr/local/bin in different primary partitions. Can I install 9.10 and use existing /home and /usr/local/bin for it ?

---

### Post by 3rag0n on 2009-12-05
Sure.

---

### Post by Paqman on 2009-12-06
> **Physicist said:**
> What if I want to use the same configuration files for my softwares, e.g., I do want the same .emacs, etc. ?


You could copy an existing .emacs folder into another account, but you'll have to change the owner of the folder to get it to work for that user:
```
sudo chown -R username:username /home/.emacs
```

That will give you the same settings in both accounts.

---

