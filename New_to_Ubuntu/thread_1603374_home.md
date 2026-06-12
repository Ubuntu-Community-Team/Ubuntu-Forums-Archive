---
title: "/home"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by spillage2 on 2010-10-22
I have set up 10.04 on all my systems now but have not set up my /home in a separate partition.

Can this be done now or would I have to completely reinstall the os from scratch.

Not very good with command lines yet so if it is possible to move my /home directory a few simple pointer would be helpful.

---

### Post by JBAlaska on 2010-10-22
This is the best [Guide](http://psychocats.net/ubuntu/separatehome) that I know of for doing this. Just go slow and you'll do fine.

---

### Post by spillage2 on 2010-10-22
thanks for the link looks like just what im after although i started to follow the instructions but due to me having two hd i kinda got lost.

i will sit down and have a proper look tomorrow to get my head around it and not end up changing the name of my /home folder and messing things up.

Cheers,

Spill.

---

### Post by ArgusVision on 2010-10-22
Looks like a really good link. One small thing you probably already know, where it says **mount -t ext3** you'll probably want to use **ext4** if thats the format you used. ( -t in this case indicates file format)

---

### Post by spillage2 on 2010-10-23
Ok been looking at his today. But am getting stuck.   When I make my new directory to copy my /home to it always creates this in the old partition.  I have /dev/sda1 and /dev/sda3.  Rather than $sudo mkdir /newhome/ do I do $sudo mkdir /dev/sda3/newhome/.  Then  $cd /home/ $find . -depth -print0 | cpio --null --sparse -pvd /dev/sda3/newhome/  Sorry very green when it comes to the command line.

---

### Post by ArgusVision on 2010-10-24
> **spillage2 said:**
> Ok been looking at his today. But am getting stuck.   When I make my new directory to copy my /home to it always creates this in the old partition.  I have /dev/sda1 and /dev/sda3.  Rather than $sudo mkdir /newhome/ do I do $sudo mkdir /dev/sda3/newhome/.  Then  $cd /home/ $find . -depth -print0 | cpio --null --sparse -pvd /dev/sda3/newhome/  Sorry very green when it comes to the command line.

Ok. The problem started at the "Rather than ..."
Follow the Guide. There's a reason the writer has you create the **/new** directory and mount the **/dev/sda3**. In order to copy to the files you must do this. The path **/dev/sda3** *is* the hard drive you want to write to, but Linux sees it as a special file. You must mount it in order to write into it. "mkdir /dev/sda3/newhome probably returns an error, no?

Please, follow the guide step by step. I don't know the writer personally, but from reading the guide he seems to know what he's doing.

---

