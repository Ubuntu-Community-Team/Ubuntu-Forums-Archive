---
title: "Software Manager not working due to multiple managers running?"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by res.being on 2010-08-25
Greetings! :) I just installed Karmic Koala/ Ubuntu 9.10 on a system that used to be 100% Vista. The software center's not letting me install anything as supposedly other programs are running. After way too much research, i opened the equivalent to Window's Task Manager, but no process on their mentioned anything about software managing. Software Manager (or Synaptics) keeps giving me a sudo command to do manually, but unless i'm entering it wrong, i'm getting nowhere with it. 

Here's the error msg that pops up whenever Synaptics is opened:
> E: dpkg was interrrupted, you must manually run 'sudo dpkg -- configure -a'
E: _cache->open() failed, please reportSo anyhow, i'll be unable to install anything until you fine people hopefully help me!

Just to warn you, **i'm totally new to Linux **& not at all familiar with terminal & all the other technical stuff (in general, not just the Linux sort) that seem to be required knowledge to keep things from crashing spectacuarly. Feel more than welcome to ask for more info, or tell me to do a simple task, but please explain how. [Even with code boxes, please state if any character really means something other than entering said character in. Line breaks i interpret as designating 'enter key' ... anything else i'll just try to duplicate into terminal & hope nothing bad results from it] 

And seriously, I'll be way happier being treated as brainless & clueless than getting confused & discouraged by incomprehensible instructions. So many thanks in advance for understanding & understandable responses, or even any at all!

P.S. There was a somewhat similar problem in a thread that came up searching the forum, but to be quite honest it seemed as if half of it was in Latin (except less understandable, due to lack of common word roots). And please move this if this is in the wrong forum ... it just seemed best to post here for the time being, due to my lack of familiarity with almost everything Linux related.

---

### Post by Peter09 on 2010-08-25
So when you open a terminal and run this command

```
sudo dpkg -- configure -a
```

what happens?

---

### Post by res.being on 2010-08-25
> Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
When i enter in 'dselect;, it says it's not installed, & also that 'dselect' isn't a valid command ... (also, i have no clue what it means by 'pipe it through')

---

### Post by silverglade00 on 2010-08-25
I think that command should be:

```
sudo dpkg --configure -a
```

Note the lack of a space character between -- and configure.

---

### Post by inameiname on 2010-08-25
This error and command pops up for me from time to time. It's easily resolved if you just do it. At least is the case with me.



sudo dpkg --configure -a

---

### Post by res.being on 2010-08-25
Wow ... I'm quite impressed with the difference a space can make!

Uhm, it seems to be doing a lot; tho at one point this came up, & i'm wondering if it's a serious problem:
> Setting up binfmt-support (1.2.14) ...
Installing new version of config file /etc/init.d/binfmt-support ...
update-binfmts: **warning: /usr/share/binfmts/c**li: no executable /usr/bin/cli
found, but continuing anyway as you request  [bolded text mine]

Also, is it vital to have Java environment installed?

Should i keep the terminal open after it said this? >  Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place The software manager does seem to be working!! ^_^

[Sorry for asking lotsa questions about every other thing that flashes on the screen like a toddler sitting on the lap of a computer user trying to go about their normal business ... just want to be sure everything's running smoothly after my laptop's recently recovered from seeming near-death! Thanks **muchly** for all the assistance, btw!]

---

