---
title: "Syncronization operation betn two directories"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by tanmoy.talukdar on 2009-04-29
The situation is like this..
I have two folders A and B.
everything that is in B , is in A too. , but A contains much more files than B.
I 'll have to delete those files from A , which are already in B

the size of the directories are huge , 3GB and 1.5 GB respectively and there are thousands of files

what I ve done is that I have run the command "ls B > list" so now the file "list" contains all the files I need to remove. Now I m stuck what I want is to run "rm" with parameters taken from the file "list" how can I do it? pls help.

---

### Post by abhiroopb on 2009-04-29
I'm a little confused by your description. but I think basically what you are saying is that you want A and B to have different files, and in order to do that you need to delete all the files in A that are also in B.

One thing I could suggest is rsync. This is mainly a backup tool, but since it is used to sync data between two locations it may be of help...have a look at my guide: [http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html)

The "exclude" and "delete-excluded" commands may be able to help.

what is the folder structures like? or is A and B just two folders with thousands of files in them?

---

### Post by tanmoy.talukdar on 2009-04-30
> **abhiroopb said:**
> I'm a little confused by your description. but I think basically what you are saying is that you want A and B to have different files, and in order to do that you need to delete all the files in A that are also in B.

One thing I could suggest is rsync. This is mainly a backup tool, but since it is used to sync data between two locations it may be of help...have a look at my guide: [http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-use-rsync-for-backup.html)

The "exclude" and "delete-excluded" commands may be able to help.

what is the folder structures like? or is A and B just two folders with thousands of files in them?
Thanks for your support.

Though I was able to solve the problem myself, after a few minutes of googling. Basically as I told, the problem was reduced to remove a list of files.

so what I did , is I typed.. ***xargs rm < /home/tanmoy/list1*** in terminal as root (i needed root 'cause the files were synaptic packages) and Bingo!!!

(the file /home/tanmoy/list1 contained the list of files to b deleted)

---

