---
title: "mv command mistake made invisible files"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by tyoungblood on 2011-03-06
I used mistakenly used mv filename.odt /test2/ command rather than mv filename.odt /test2/filename.odt 

now the files that I moved aren't visible in nautilus but they appear as "." and ".." when I use the ls -la command in the test2 folder in terminal. Is there anyway to change the files names so I can get them back? Any help is appreciated.

---

### Post by Rakeshvijayan on 2011-03-06
> **tyoungblood said:**
> I used mistakenly used mv filename.odt /test2/ command rather than mv filename.odt /test2/filename.odt 

now the files that I moved aren't visible in nautilus but they appear as "." and ".." when I use the ls -la command in the test2 folder in terminal. Is there anyway to change the files names so I can get them back? Any help is appreciated.


if you are using gui go to test folder  From menu bar you can see the View button and from the drop down list there is an option to show hidden file
try it

---

### Post by zenwalker on 2011-03-06
. = current directory
.. = parent directory

Thats the konsole notation. You cant change that.

Just use the cp command to do your job.

Ctrl + H key should help you to make hidden file visible. Same combo will make it hidden too.

---

### Post by uRock on 2011-03-06
> **tyoungblood said:**
> I used mistakenly used mv filename.odt /test2/ command rather than mv filename.odt /test2/filename.odt 

now the files that I moved aren't visible in nautilus but they appear as "." and ".." when I use the ls -la command in the test2 folder in terminal. Is there anyway to change the files names so I can get them back? Any help is appreciated.
If all you have is a folder with the following output, then there are no files in the folder.
```
uRock@uRock-desktop:~$ ls -a ~/Empty*
.  ..
uRock@uRock-desktop:~$
```

---

### Post by tyoungblood on 2011-03-06
when I issue the ls -la command this is what I get:

total 72
drwxr-xr-x 2 name name    4096 2011-03-06 22:04 .
drwxr-xr-x 4 name name    4096 2011-03-06 18:37 ..
-rw-r--r-- 1 name name  23868 2011-02-24 15:41 chap_3.odt
-rw-r--r-- 1 name name  40117 2011-03-06 16:38 sg_vocab.odt


any idea what the first two lines are?

and when I do ls -a -i

I get:

262850     134609     163336 chap_3.odt   267387 sg_vocab.odt


I want to believe the first two sizes represent the "missing" files

---

### Post by uRock on 2011-03-07
The numbers listed with the single file are inode identifiers used by the file system management. zenwalker explains the meaning of the . and .. in the third post. Is this some kind of homework project?

---

### Post by tyoungblood on 2011-03-07
notes for a midterm coming up Tuesday...I feel like an idiot right now

---

### Post by zenwalker on 2011-03-07
When i tried the same mistake with mv as you did on natty here. It does move the file to that directory. I didnt loose the file. I guess you did some thing else or perhaps deleted it later.

---

### Post by uRock on 2011-03-07
> **tyoungblood said:**
> notes for a midterm coming up Tuesday...I feel like an idiot right now
If you are using the text for Linux 101 that I used, then that chapter should be easy to follow. [http://www.amazon.com/Introduction-Unix-Linux-John-Muster/dp/0072226951/ref=sr_1_3?ie=UTF8&qid=1299474989&sr=8-3](http://www.amazon.com/Introduction-Unix-Linux-John-Muster/dp/0072226951/ref=sr_1_3?ie=UTF8&qid=1299474989&sr=8-3)

---

### Post by tyoungblood on 2011-03-07
> **zenwalker said:**
> When i tried the same mistake with mv as you did on natty here. It does move the file to that directory. I didnt loose the file. I guess you did some thing else or perhaps deleted it later.

I wish, but I know I didn't delete the files

---

### Post by zenwalker on 2011-03-07
Then i am sure the command MV shouldn't be blamed here. Its perfectly an human error.

---

### Post by Old *ix Geek on 2011-03-07
> **tyoungblood said:**
> I know I didn't delete the filesOkay, let's go back to the beginning.
> **tyoungblood said:**
> I used mistakenly used mv filename.odt /test2/ commandIs that LITERALLY what you typed? With the leading slash in **/test2/**?

If so, go to your root directory (/) and type:
```
ls -l
```

Is /test2 listed?

If it is, cd into it:
```
cd /test2
``` (Yes, I KNOW the leading slash isn't necessary here if the OP is in root, but we're JUST MAKING SURE.)

Now, what does **ls -al** show?

---

### Post by tyoungblood on 2011-03-07
> **Old *ix Geek said:**
> Okay, let's go back to the beginning.
Is that LITERALLY what you typed? With the leading slash in **/test2/**?

If so, go to your root directory (/) and type:
```
ls -l
```

Is /test2 listed?

If it is, cd into it:
```
cd /test2
``` (Yes, I KNOW the leading slash isn't necessary here if the OP is in root, but we're JUST MAKING SURE.)

Now, what does **ls -al** show?

Thank you very much! I got one of my documents back but since I used the command twice I overwrote one of my files. I guess half is better than none. Thanks to all of the posters

---

### Post by Old *ix Geek on 2011-03-07
> **tyoungblood said:**
> Thank you very much!You're welcome. :D

---

