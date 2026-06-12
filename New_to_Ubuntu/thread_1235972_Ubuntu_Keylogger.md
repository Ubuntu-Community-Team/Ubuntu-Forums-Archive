---
title: "Ubuntu Keylogger"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Benjaminbarnes on 2009-08-09
I very recently was introduced to Linux and I am the father of a 14 year old boy. This is our only computer and I am looking for a Keylogger so that I may monitor my sons activity. I haven't had Ubuntu for long at all (maybe a week) and I'm a complete "newbie". I have come across a few Keyloggers but I still don't know how to install things unless its a step by step guide. I was wondering if some one could guide me through getting one and setting it up.

Thanks

---

### Post by mrgreggie on 2009-08-09
Found this on the forums, hope it helps.
[http://ubuntuforums.org/showthread.php?t=427829](http://ubuntuforums.org/showthread.php?t=427829)
There's specific info on page 2.

---

### Post by Benjaminbarnes on 2009-08-09
> 1.download the .tar.gz
2.extract it (either right click > extract here or in terminal **tar zxvf *<filename>***
3.go to the folder (lkl)
4.in terminal: **./configure**
5.when done, use the command **sudo make install**                                                                                               __________________ 
I got all of it done, but I am still confused on step 5. What does sudo do and where do I enter it in to?

---

### Post by juancarlospaco on 2009-08-09
> **Benjaminbarnes said:**
> I got all of it done, but I am still confused on step 5. What does sudo do and where do I enter it in to?

[**Click Here **]("apt:/lkl")
:)

---

### Post by MoebusNet on 2009-08-09
First, a disclaimer. I'm not a command-line expert, but I'll try to answer your questions.

1) sudo is the command that will give you "super-user" otherwise known as "root" privileges. This is a very powerful command that allows you to modify or eliminate any part of your Ubuntu installation so it should be used cautiously and treated with care. Check, recheck and triple check your commands when you are the super-user because if you make a mistake the computer will do exactly and precisely what you told it to, even if it breaks your Ubuntu installation.

2) You enter sudo and any commands that go along with it in "Terminal". You click on Applications>Accessories>Terminal which opens a command line screen sort of like the DOS screen in Windows. You type in, for example,

sudo make install <*filename*>

all on the same line. Then use the "Return" (also known as "Enter" key).

Here is a link to the Psychocats tutorial on Terminal and sudo. It explains it better than I can:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

When you do this the terminal will ask you for the password you set up for your Ubuntu installaton to verify that this is really you and that you really want to do this. Enter your password and use the "Enter" key.

The commands you entered will now execute. Hope this helps.

---

### Post by overdrank on 2009-08-09
I probably should not chime in but oh well. I am a father of a 17 year old son so I have  limited experience and I think you can just monitor the son instead of keylogging. Just my 2 cents :)

---

