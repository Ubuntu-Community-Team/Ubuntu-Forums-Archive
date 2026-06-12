---
title: "deleting folder as root"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by ideologo on 2008-12-17
Trying to convert the installation file Adobe Reader .rpm to a .deb file it did not work. It create a folder that I can not delete even as root and it prevents me to retry the installation. Does anybody know how to delete a folder as root even if the folder (or directory) is not  empty.
Thanks and merry christmas!):P

---

### Post by rzrgenesys187 on 2008-12-17
```
sudo rm -r directory
```

Replace "directory" with the name of the folder and that will get rid of it.  Note "-r" removes the directories and anything contained within them recursively.  BE CAREFUL, the folder doesn't go to trash

Alternately,

```
gksu nautilus
```

From the terminal or after typing Alt+F2 will open your file browser as a root and you can delete it that way, probably a bit safer.

---

### Post by starcannon on 2008-12-17
prepend your rm command with sudo
or you can run nautilus as gksudo for the chore as well.
Either way be absolutely sure what your deleting.
```
gksu nautilus
```
for the rm command I'd prefer to send you to the man pages, 
```
man rm
```
Please make sure you don't delete something valuable to yourself, and remember for the specific task your enquiring about you likely need to use sudo.

GL

---

### Post by sosaudio1 on 2008-12-17
> **ideologo said:**
> Trying to convert the installation file Adobe Reader .rpm to a .deb file it did not work. It create a folder that I can not delete even as root and it prevents me to retry the installation. Does anybody know how to delete a folder as root even if the folder (or directory) is not  empty.
Thanks and merry christmas!):P

Use this command for your directory in CLI

rm -rf whatever your directory is


BUT WORD OF CAUTION!!!!!!!! BE ABSOLUTELY SURE THAT YOU HAVE THE RIGHT DIRECTORY

PEACE

---

### Post by xjcannonx on 2008-12-17
you can always relpace the rm with ls and it will show you what you are about to delete

---

### Post by Huszarnyi on 2012-08-14
Using ```
gksu nautilus
``` achieves the job perfectly and is much more safer than other methods, in my opinion.

---

### Post by dodo3773 on 2012-08-14
> **Huszarnyi said:**
> Using ```
gksu nautilus
``` achieves the job perfectly and is much more safer than other methods, in my opinion.

This thread is almost 4 years old friend. I think they may have lost interest

---

### Post by Perfect Storm on 2012-08-14
Necromancing is a forbidden art on these forums.


Thread closed.

---

