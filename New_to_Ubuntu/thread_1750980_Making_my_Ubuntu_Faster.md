---
title: "Making my Ubuntu Faster"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by meadhikari on 2011-05-06
What could be some tweaks to make my system faster?

I have 2 GB of RAM and Intel 2.5 GHz Dual core.

System is too slow at start up and copying to USB drive is very slow too.

Will any other Ubuntu[currently 11.04] variant be better suitable for me, my primary task are in vlc, wine, gedit and sometimes with eclipse.

Thanks in advance

---

### Post by HereInOz on 2011-05-06
It is a bit difficult to judge based on what you say, as we don't know what your concept of "slow" is.  

If the system really is slower than it should be, in boot up and copying to USB, then I suspect that you may have a hardware issue.  Is this a new hardware build, or is it a Windows reject which is being pressed in to service as a Linux machine?

If the latter, was it condemned for being slow in Windows as well?

I know that some people have an expectation that Linux will be "lightning fast" compared with Windows on the same hardware, but that isn't the case.  It is generally quicker, by quite a bit, but it doesn't "fly" so to speak.

How long does it take to boot up?

---

### Post by meadhikari on 2011-05-06
About a month or two ago things were fine.
No comparison with windows here.

Thank pink background with ubuntu written in white and blip blip [at start up] stays for far more time then it previously use to be.

Is there any tweaking that I could do to make it faster?
Deleting some not so important start up activities or some other things?

What may be other reason which make a system go slow with time?
Would switching to other ubuntu variant solve my problem?

---

### Post by vanquishedangel on 2011-05-06
> **meadhikari said:**
> About a month or two ago things were fine.
No comparison with windows here.

Thank pink background with ubuntu written in white and blip blip [at start up] stays for far more time then it previously use to be.

Is there any tweaking that I could do to make it faster?
Deleting some not so important start up activities or some other things?

What may be other reason which make a system go slow with time?
Would switching to other ubuntu variant solve my problem?

No promises here but just my 2 cents

I have 3 computers here, 2 hp dc7100 and 1 compaq presario 1500us

here is a link to a post i did with my computers and upgrading

[http://ubuntuforums.org/showthread.php?t=1744050](http://ubuntuforums.org/showthread.php?t=1744050)

I am not sure if you computer beats mine or not but i use lubuntu because it is way more efficient and it is available in the repositories, then on boot up I choose LXDE. You have all the functions of a regular ubuntu just not as heavy of a load ( i also use lxdm instead of gdm, you get that option when you install lubuntu)

PS lubuntu is not an official supported release but it is community supported below is a screenshot of my desktop

[http://i750.photobucket.com/albums/xx143/itstherealshawn/Screenshot.png](http://i750.photobucket.com/albums/xx143/itstherealshawn/Screenshot.png)

---

### Post by mastablasta on 2011-05-06
> **meadhikari said:**
>  
I have 2 GB of RAM and Intel 2.5 GHz Dual core.
 
 
important data is missing here:
 
1. what kind of graphics card do you use? do you have proprietary dirvers installed for it?
2. How much of your hard disk is still free?
 
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by HereInOz on 2011-05-06
If you have the same system as you did a couple of months ago, and it just got slower, then I still suspect a hardware problem.  Ubuntu doesn't slow down much as it gets older, so unless the OS has really broken something, you have a hardware issue.

Check out the hard disk activity when booting.  Is it thrashing furiously while nothing much is happening on the desktop?  Does the hard disk grind forever while you are loading programs which used to load quite snappily?  

If so, tends to indicate a hard disk problem.  You could try cloning it to a new HDD before it fails irrevocably. Use Clonezilla - works well.

If there is no, or minimal, hard disk activity, but nothing is happening on the desktop, then I would suspect either a RAM or motherboard problem. In this case, if you have access to another machine, pull the hard disk out of your computer and put it into the other computer and see how it runs.  

Linux will usually boot up happily on different hardware, and if it runs better on the other machine, then there is an "on-board" issue.

If, after all this, the system still runs like a dog with a cloned hard disk, and on different hardware, then there is probably an OS breakage somewhere.  The real techo guys would guide you on how to perhaps repair that - it is beyond me, unfortunately.

Good thought on the hard disk space, mastablasta

---

### Post by meadhikari on 2011-05-06
320 GB Hard disk and 80GB still free

No idea on what sort of graphics card I have :( [no access to computer now.]

---

### Post by idoitprone on 2011-05-06
```
lspci
```

---

