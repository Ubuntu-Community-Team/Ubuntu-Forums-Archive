---
title: "Deleting Simple Backup folders"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by s1wood on 2011-01-11
I have been trying out backup programs, with limited success.
My immediate question is, how do I get rid of the folders already created by Simple Backup on my 2nd disk - they are locked, and I don't have permissions.  These are duplicates that were just created during my tests with the system so I would rather get rid of them.

Susan

---

### Post by Jeruvy on 2011-01-11
In most cases a simple 'remove' should get rid of them, but you may need root permission to do so.  

```
$ cd /path/to/backups/ #change path to backups to your folder
$ ls -al
```

That will show you who owns the files.

```
$ sudo rm -rf folder/ #change folder to your folders name
```

That will delete all the folders and their contents in 'folder/'.  *Be careful with this command as it does permanently delete files!* So ensure you are deleting what you want.  

So copy and paste the above commands and edit appropriately for your needs.  If they fail to resolve this, please provide the output from these commands so we can review what happened and what to do next.

Good luck,

---

### Post by s1wood on 2011-01-18
Thank you for the advice,
I didn't actually follow it because I am a bit wary of complicated command lines but I decided I ought to make the attempt so I went  do some homework on the subject first and eventually found  one of the Ubuntu Community Doucumentation sites  which included this:. 
[I]
[/I]*>Create a [launcher]("https://help.ubuntu.com/community/HowToAddaLauncher") with the following command: *
*gksudo "gnome-open %u"**When  you drag and drop any file on this launcher (it's useful to put it on  the desktop or on a panel), it will be opened as Root with its own  associated application. This is helpful especially when you're editing  config files owned by Root, since they will be opened as read only by  default with gedit, etc. <*

This opens my folders and has allowed me to delete them.
 I posted this for the benefit of others who haven't managed to read that far either.  I will go back and try out the other command for the experience though.

regards

Susan

---

