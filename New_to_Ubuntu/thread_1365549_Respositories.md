---
title: "Respositories"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by HeadlessFrog on 2009-12-27
Hi I just ran update manager for the first time and ubuntu told me that not all the respositories could be found i'm connected to the Internet though so I'm not sure what to do. Also upon loading windows for the first time I was told to restart due to driver problems after i set my dual boot up and the error report told me I had a blue screen which I hadn't I installed windows first too.

---

### Post by drs305 on 2009-12-27
Welcome to the Ubuntu forums HeadlessFrog,

For the repository question, please post the error messages. Most often the messages are either requesting a key (which can be added easily from the command line), telling you the site is unavailable, or that one or more of your repositories cannot be reached.

If you provide the error messages we can provide the solution. If the problem is related to what's contained in /etc/apt/sources.list we will probably ask you to post the contents of that as well.

---

### Post by HeadlessFrog on 2009-12-27
> **drs305 said:**
> Welcome to the Ubuntu forums HeadlessFrog,

For the repository question, please post the error messages. Most often the messages are either requesting a key (which can be added easily from the command line), telling you the site is unavailable, or that one or more of your repositories cannot be reached.

If you provide the error messages we can provide the solution. If the problem is related to what's contained in /etc/apt/sources.list we will probably ask you to post the contents of that as well.

Ok well it said hat either I didn't have a connection to the Internet which I do since it was downloading and all it also said that I may have to change the URL in order to get some of the respositories if possible though where would I find these error reports? Or is this enough info? I'm also havin problems with grug right now it's telling me that: A new verison of configuration file /etc/defuLt/grub is availible but the verison installed currently has been locally modified I picked the show me side by side option or the show me diffrence verison can't remember which but I'm not sure If I picked the right one or if there's A way to undue it it's been saying configuring grub pc for forever Now and it seems to want me to restart to finish installing updates As well. Would you know of any good noob guides for ubuntu too?

---

### Post by Mahngiel on 2009-12-27
If you look at the top of this forum sub-topic, there's a great pdf for you to download and read up on.

if you went into Software Sources, you could check-mark the repositories you are unable to download from

I would recommend updating to grub2, and not using grub-pc.
'sudo apt-get install grub2'

---

### Post by HeadlessFrog on 2009-12-27
> **Mahngiel said:**
> If you look at the top of this forum sub-topic, there's a great pdf for you to download and read up on.

if you went into Software Sources, you could check-mark the repositories you are unable to download from

I would recommend updating to grub2, and not using grub-pc.
'sudo apt-get install grub2'

Ok I now have 2 ubuntu installs listed inGnu grub 1.97 beta 4 one is 2.6.31-16-generic the other is 2.6.31-14-generic why do I have 2 now? It's insane how annoying it is typing on an iPod touch

---

### Post by kansasnoob on 2009-12-27
> **Mahngiel said:**
> If you look at the top of this forum sub-topic, there's a great pdf for you to download and read up on.

if you went into Software Sources, you could check-mark the repositories you are unable to download from

I would recommend updating to grub2, and not using grub-pc.
'sudo apt-get install grub2'

The package "grub-pc" is grub2. The package "grub2" is (from package description):

> This is a dummy transitional package to handle GRUB 2 upgrades.  It can be
safely removed.

---

### Post by kansasnoob on 2009-12-27
> **HeadlessFrog said:**
> Ok I now have 2 ubuntu installs listed inGnu grub 1.97 beta 4 one is 2.6.31-16-generic the other is 2.6.31-14-generic why do I have 2 now? It's insane how annoying it is typing on an iPod touch

That's normal. They're two different kernels, it's generally a good idea to keep at least two working kernels.

drs305 wrote an excellent guide regarding grub2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It may seem a bit overwhelming at first, so feel free to ask questions.

---

### Post by HeadlessFrog on 2009-12-27
> **Mahngiel said:**
> If you look at the top of this forum sub-topic, there's a great pdf for you to download and read up on.

if you went into Software Sources, you could check-mark the repositories you are unable to download from

I would recommend updating to grub2, and not using grub-pc.
'sudo apt-get install grub2'

Uhoh accoring to that PDF you shouldn't run ubuntu x64 with windows x86 which I'm doing now should I just reinstall altogther then? What's the harm in it anyways I have an x64 bit processor anyways.Also do I just load the latest kernel then kansasnoob?

---

