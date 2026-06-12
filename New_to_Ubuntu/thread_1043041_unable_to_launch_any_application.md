---
title: "unable to launch any application"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by fuser312 on 2009-01-18
its strange, i could open some apps like browser or terminal, but i am unable to open some tools like azuerus, synaptic, amarok etc. it seems that they are starting but they won't. 
i got this error while trying to run synaptic:

> failed to run /usr/sbin/synaptic as user root (although i am running it as a normal user) unable to copy user's Xauthorisation files

i think the problem is that, i made two large torrent download at night, and went to sleep, and as i don't have enough space in ubuntu partition, some problem might have occur.
as in morning i started ubuntu, the x server refused to start with no error message. so, i went to recovery mode and checked the option "try to clean space" (thinking that it might be a space related problem due to thoose downloads). but now, i have got this problem. is that cleaning space in recovery mode has deleted some important files??. if yes, how could i get them back or any other methods please.

i have only 800 mb left with my ubuntu

---

### Post by The Cog on 2009-01-18
That 800M may be the space that ext3 reserves for root only. I suggest you try to delete one of those big torrent files using recovery mode. You need thesse commands to be able to find and delete the file:
**pwd** : print working directory - tells you where your command prompt is
**cd <dirname>** : change to a directory, e.g. cd /home/myname
**ls -l** : list the files in the current directory (long format, one per line)
**rm <filename>** : remove a file

P.S.
Rather than all that cd and pwd stuff,if you know the filename, you can just do something like:
**rm /home/myname/Desktop/big-download.mpg**

---

### Post by fuser312 on 2009-01-18
hey thanx cog,
my problem is solved, i solved the problem through recovery mode.
wondering how to mark it solve

---

### Post by stderr on 2009-01-18
> **fuser312 said:**
> wondering how to mark it solve

Following some stability problems with the forums, the plugins allowing marking threads as solved and thanking other users have been temporarily disabled. They'll be back soon-ish, so I understand :P

---

