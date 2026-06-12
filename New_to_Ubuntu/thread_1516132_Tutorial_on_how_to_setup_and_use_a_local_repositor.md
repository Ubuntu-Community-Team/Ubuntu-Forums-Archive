---
title: "Tutorial on how to setup and use a local repository"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by newbie01.linux on 2010-06-23
Hi all,
 
Am a newbie on Linux and Ubuntu seems to be the easiest one to use. 
 
I want to know if anyone can suggest a tutorial link that shows how to set up a local repository, preferably one that shows how to do it step by step in the most simplest steps possible.
 
My internet bandwidth is very limited so I want to have a local repository to which I can save all downloaded packages so that in case I have to install Ubuntu on another machine, I can just copy those packages from one machine to another instead of downloading them again.
 
I've seen several threads of the same topic/subject but am finding it hard to follow the steps suggested on those threads.
 
Any response will be very much appreciated. Thanks in advance.

---

### Post by mk1w86 on 2010-06-23
Having a local mirror of the Ubuntu repository would not be ideal if you have limited bandwidth because it requires large downloads to keep all the packages up to date.

I would recommend something such as APTonCD which will allow to install packages you have downloaded once on many machines:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

There are also other methods which allow you to download packages designed for offline installation:

[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

---

### Post by Paqman on 2010-06-23
If your bandwidth is limited, setting up a local mirror is not a great idea. The repos are about 60GB to download, plus constant updates.

All the packages you download and install are cached in /var/cache/apt/archives anyway. Just copy the contents of that folder over to your new machine. Another option is to use [APTonCD]("http://aptoncd.sourceforge.net/").

---

### Post by stinkeye on 2010-06-23
I have used the method outlined in [**_this[COLOR="DarkRed"][/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1326771") thread.
See post #4. Instead of a hard drive I just used a usb stick.

---

### Post by newbie01.linux on 2010-06-24
> **stinkeye said:**
> I have used the method outlined in [**_this_**]("http://ubuntuforums.org/showthread.php?t=1326771") thread.
See post #4. Instead of a hard drive I just used a usb stick.


Thanks for your reply, am leaning towards using the USB portable disk ... have read the thread that you recommended, good thing I read the whole thread ... 

Am about to ask how to tell apt to start checking the USB first and just noted that underneath is the /etc/apt/source.list file ... ;)

Will check on the APTonCD as well as recommended by others ...

---

