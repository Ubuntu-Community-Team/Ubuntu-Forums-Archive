---
title: "access home folder after copy/paste to new hd install"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by MichaelSM on 2009-03-22
Hi to the Forums again.

I have a 40G hd with 8.10 on it, and it is nearly full.

So I installed 8.10 on a spare 80G hd, then connected both drives in one computer.

Copy/pasted 29G of home directory into the new hd's file system, which required root privilege to do so. On the new hd if you get what I mean.

Same with lib, etc, and usr.

The new hd boots up well, but I have to OK a little window which mentions that my settings aren't accessible until I enable user rights to the home folder.

Then, once I've got a Desktop, I can sudo nautilus, navigate to the 'old' home folder, and there's everything I pasted there.

So, what command is required to give user rights to that folder? (Plus perhaps the other ones I mentioned)

I hope I've explained this scenario correctly.

Help appreciated.

Cheers,

Mike.

---

### Post by diablo75 on 2009-03-22
You might trying opening up nautilus as root with this command in terminal:

```
gksudo nautilus
```

And once you do that, open the properties for the folders you moved with a right-click>properties, and then the permissions tab, and change the owner of that folder (and all sub-folders/files) to yourself... Though I can't promise that this will do the trick.

---

### Post by James_Lochhead on 2009-03-22
Open a terminal and type:

```
sudo chown -R <your username> /path/to/old/home/folder
```

Shove your username and the path to your old home folder in and it should be fixed.

---

### Post by MichaelSM on 2009-03-22
Thank you James and Diablo.

The new hard drive is at this moment installing many megs of updates, so I'll give your suggestions a go in a few minutes.

It's likely that I took a ham-fisted approach to the whole issue.

Please watch this thread if you can.

I'll post whatever I can ASAP.

Greatly appreciated.

Mike.

James,re. your command 

sudo chown -R <your username> /path/to/old/home/folder

after -R is there a space before 'michael' (my username) or a slash?

---

### Post by MichaelSM on 2009-03-22
'noperand'

What am I doing wrong?

Mike.

---

