---
title: "Please help the newbie"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by masella on 2009-02-16
hey all, brand new user here with some problems.

I have an hp pavilion zv5000 laptop.  Ubuntu 8.04 is installed as a partition on my hard drive.  I cannot, for the life of me, get it to access the internet though.  I saw a similar topic here, but wasn't sure if I should start my own thread or not.

additionally, during the installation, I resized my XP partition and followed the instructions to get myself available space for Ubuntu, but since the installation (all run from the CD) I haven't been able to start up my XP partition successfully.  Thankfully, all my files are backed up on an external hard drive, but I would like to know if there is anyway I might get that working again?

---

### Post by alpage2 on 2009-02-16
There are a couple of different problems here.

First - the Windows problem - when you boot the laptop, do you see a grub boot menu listing both ubuntu and windows as choices? And when you select windows, what exactly happens?

Second - how are you expecting to connect to the internet? Dial-up? Wireless broadband?

If the latter post the output from the lspci command, and from the iwconfig command.

Regards
Alan

---

### Post by TJCIB on 2009-02-16
Hello and welcome!

First a few recommendations:
1) make your subject something descriptive so people can know what your problem is about, that way people with the right knowledge will read your post.

2) Keep your post to one topic.  Yours here covers two very different topics, one is called "dual boot", the other is getting something in Ubuntu to work.

I will attempt to help with the dual boot part of it.  I would recommend using Google and searching your network card model and "ubuntu" and it usually comes up with some great troubleshoot pages.  You also didn't say if it was wireless or not, which will make a difference.

If you could give a little more information about your system and how you installed Ubuntu.  I am assuming you had XP installed on your laptop and then used the partition tool that comes with the Ubuntu installer to repartition your hard drive.  Did you use "Guided" or "Manual"?

If you could open a terminal (Applications>>Accessories>>Terminal) and copy and paste the following command
```
sudo fdisk -l
```
Which will show us all the partitions on your computer.  Copy and paste the output here, highlight the text, and click on the little "#" sign on the top.

Also, can you describe what happens when you turn on your computer.  Do you get a menu giving you the option to select either Ubuntu or XP (and maybe some other options)?  (This is the GRUB menu)

If you select XP, what happens, do you get any errors?

Thanks.  You description will help diagnose the problem.

*arg* Alpage beat me!!  hehe

---

### Post by hyper_ch on 2009-02-16
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

