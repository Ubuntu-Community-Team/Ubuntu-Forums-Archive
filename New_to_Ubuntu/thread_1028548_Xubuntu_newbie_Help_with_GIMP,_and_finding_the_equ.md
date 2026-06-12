---
title: "Xubuntu newbie: Help with GIMP, and finding the equivalent of certain winxp functions"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by samsam_eli on 2009-01-02
I am a complete newbie to Linux, so if you help me, please remember to spell things. Use small words ;-) 

First, some facts:
I have a used Dell computer. Some firm was replacing their computers, so my sis got hold of one for me.
She has installed Xubuntu.

My Problems:
1. I can't find certain info about programs. I'm used to WinXP but can't find it in my Xubuntu. Examples: 
 a. what version of xubuntu I'm using
 b. How many bits my computer is using?
 c. Where do I defragment or use the disc clean up?

2. where and what is the equvalent of the "run" command in Windows?

3. I can't download the gimp-help-en file
4. When I first opened GIMP there was a window for choosing colours and viewing history etc. I can't find it
5. How can I run Windows programs on Xubuntu?

---

### Post by chrisod on 2009-01-02
> a. what version of xubuntu I'm using

It's in the 'about" option under the "system" menu.
> 
b. How many bits my computer is using?

If it's a older used system it's most likely 32 bit.

> c. Where do I defragment or use the disc clean up?

You don't need to defrag in Linux.
> 
2. where and what is the equvalent of the "run" command in Windows?

The terminal window can be found at Applications menu -> System -> Terminal.  There really isn't a direct corollary in Linux to the run command., If you want to start a program from the command line simply type the name.

> 4. When I first opened GIMP there was a window for choosing colours and viewing history etc. I can't find it

It was probably minimized to your toolbar. It doesn't stay docked to the edit window.

> 5. How can I run Windows programs on Xubuntu? 

You don't. Wine can sometimes maybe run a Windows program, but it's very hit or miss on how well it will run, if it runs at all. There are Linux equivalents for just about anything you can do in XP. The primary exception IMHO is video editing, which is still much better in XP.

Start here for more help. [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Spend some time educating yourself about Linux. It will be a very worthwhile investment of your time.

---

### Post by achase79 on 2009-01-02
alt-F2 will get a run menu

---

### Post by albinootje on 2009-01-02
> **samsam_eli said:**
> 
 a. what version of xubuntu I'm using

Open a terminal, and type :
```

lsb_release -a

```
> 
 b. How many bits my computer is using?

Open a terminal, and type :
```

uname -m

```
If it is mentioning 64 bit, then it's 64 bit, otherwise 32 bit.
> 
3. I can't download the gimp-help-en file

What's the exact error message concerning that ?

Pleas open a terminal, and do the following :
```

sudo apt-get update
sudo apt-get install gimp-help-en

```
Please report any errors.

---

