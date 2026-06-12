---
title: "file path unable to find"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by nipsy on 2010-04-23
I'm trying to share a very specific folder or two. My problem is we've moved them around so much the path has changed. Now I can go to "find" and the folder opens up, but what I want is the actual PATH it takes to get there.

example:

I have a media folder that contains all media. to get to it, I click Computer, to file system, to media.

I need it written in path form path= computer/file system/media???

Is there a command I can use to find out the exact paths of folders?? 




I cannot believe I'm posting this question, but in all fairness we have been up for nearly 2 weeks straight trying to get 9 computers in house running different OS to link up on top of building a server from scratch. I feel silly about such a small thing, but right now its holding us up and I'd love to have it answered.

Please and thank you in advance for the help yet again.

---

### Post by UltraMathMan on 2010-04-23
You can do this either by clicking on the pencil icon below the Back button in the file manager, or you can open a terminal (Applications->Accessories->Terminal) and drag the folder into the open terminal window to display the absolute path.

-Hope this helps :)

---

### Post by nhasian on 2010-04-23
> **nipsy said:**
> I have a media folder that contains all media. to get to it, I click Computer, to file system, to media.

from your description it sounds like your media folder is in your root directory so it would be /media.

a few helpful terminal commands for you:

ls - list directory contents
pwd - print working directory (basically shows you the folder your in)
locate - find files by name

---

### Post by nipsy on 2010-04-23
thank you thank you...apparently my pencil doesn't work..

but dropping it in terminal worked like a charm..

*sigh* one down, 9 more to go...

---

### Post by UltraMathMan on 2010-04-23
Glad it worked out for you!

---

