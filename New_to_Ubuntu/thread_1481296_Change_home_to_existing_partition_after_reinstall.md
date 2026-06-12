---
title: "Change home to existing partition after reinstall"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by evil_urna on 2010-05-12
I reinstalled today and because of the screaming baby I neglected to tag my existing home partition as home with the fresh install. 

I did some googleing around and I found these instructions that kinda sound like what I need.

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

My only concern is that I dont want to jack up this install with stuff from the old install. Could I merge the content from the new home dir to the old home dir and then force the system to mount the partition as home from now on by modifying the instructions in said page? 

Thanks for your help in advance

---

### Post by evil_urna on 2010-05-12
I found another set of instructions for a person who did exactly what I did.

[http://superuser.com/questions/12182/how-to-get-a-reinstall-of-ubuntu-to-recognize-home-partition]("http://superuser.com/questions/12182/how-to-get-a-reinstall-of-ubuntu-to-recognize-home-partition")

and it did not work for me. It would not mount /dev/sdb1. I removed the line with nano and I am back to normal now.

---

### Post by oldfred on 2010-05-12
Sure blame the kid. It never is the one sitting between chair and keyboard. (I know that for a fact)

I used this to move /home, you may have to skip a step or two as you already have a partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by evil_urna on 2010-05-12
> **oldfred said:**
> Sure blame the kid. It never is the one sitting between chair and keyboard. (I know that for a fact)

I used this to move /home, you may have to skip a step or two as you already have a partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Thank you very much that got it fixed.

also totally the kids fault here lol.

---

