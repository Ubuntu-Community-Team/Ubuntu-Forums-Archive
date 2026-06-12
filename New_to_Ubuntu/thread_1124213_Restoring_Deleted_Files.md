---
title: "Restoring Deleted Files"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-04-13
Hello. Had a slight accident with the 'rm' command.

I was cleaning out a few directories to make space, and since they were too big for the wastebin I used 'rm -r <directory name>' to clear them out, which I was under the impression was the correct way - I'm now guessing not, as its looped back on itself and killed everything except a few files in my home folder.

Does anyone have any idea why, or if there is a way to get the files back? All programs still seem to be working, thankfully, although wine has been cleared out.

---

### Post by Michael.Godawski on 2009-04-13
hi,

since you are saying that your Ubuntu still works, can you please run this command to find out the exact rm command you have used?

```
gedit ~/.bash_history
```If you have used sudo rm have a look here:

```
gedit /var/log/auth.log.

```> 
and killed everything except a few files in my home folderWhat do you mean by everything else?

**edit **you are using kubuntu? kate not gedit.

---

### Post by Azhtabak on 2009-04-13
The exact command was ```
rm -r
```

However, looking at the history, one of the leads reads:
```
rm -r <directory>cd/home/me
```
Which I'm guessing is where it looped round?

By 'killed', it deleted everything in the folder except a few of the hidden (.whatever) folders, though it deleted some of those too (such as .wine). It also for some bizzare reason left one folder left in my home folder that wasn't hidden, however this had been earlier copied from a usb stick, so I think it didnt' have permission to do so.

---

### Post by jrothwell97 on 2009-04-13
I hope you did regular backups.

If not, then you need to shut down the machine *immediately* and use another machine to hunt down a forensics/file recovery live CD.

---

