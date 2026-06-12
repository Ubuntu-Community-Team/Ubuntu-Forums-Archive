---
title: "big freeze"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mauro17 on 2009-12-27
hallo,
i am a very, very absolute beginner, so excuse me for the incorrect words.terms etc
Maybe there is somebody out there who could help me with ubuntu 9.10 and freezes probs. Just installed it on a sony vaio pcg-k195hp, wiped out xp and found out that it freezes after a minute or so: maybe the reason is the wireless connection? now that I am linked by cable, it seems it is ok; on the other hand I tried to download voipcheap and it went dead straight away. I selected 512 ram as opposed to 256, but I do not really knows what it means...the hard disk is 40GB...

thanks!!
mauro17:P:P

---

### Post by marin123 on 2009-12-27
what do you mean you "selected" 512 ram?

---

### Post by markjensen on 2009-12-27
Agreed with marin.  Not a lot of info provided yet.

You may very well have a problem with your wireless config. Can you provide information on what type or chipset it is (how did Linux detect it)?

Also not sure on where you can select amount of RAM on install.  Let's have you copy a line of text I will post here into a terminal you will have to open up on your computer.  It will create a text file you can post here that will show your memory configuration.

**cat /proc/meminfo > meminfo.txt**

Then make a reply in this thread and post a copy of the "meminfo.txt" file that will be created in your home directory.

---

