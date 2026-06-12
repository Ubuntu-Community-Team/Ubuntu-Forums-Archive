---
title: "Firewire issue/Kino capture/DV-SIMPLE solution required"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by MisFitt on 2010-02-23
Hi,
I had this problem weeks ago with karmic which was solved,anyway,I've installed Jaunty again because of so many issues I had and I need advice for the simplest,surest,resolution of my firewire/dv capture error in Kino and I can't remember or successfully follow the instruction I had!
-WARNING:1394 kernel module not loaded or failure to read/write/dev/raw1394!-
I'm afraid I may have messed something up trying to resolve this so I'm hoping for experienced,clear instruction to get my dv camera recognised.I feel silly because it worked a treat last time but I can't remember what did it.I've been pumping commands into the terminal,going over all the steps in my previous post that happily resolved,now fearing I may have screwed something up.
Is 64 bit possibly a different deal with these matters?

---

### Post by MisFitt on 2010-02-23
anyone?

---

### Post by 73ckn797 on 2010-02-23
See if this will help:
[http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html](http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html)

---

### Post by MisFitt on 2010-02-23
> **73ckn797 said:**
> See if this will help:
[http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html](http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html)

thanks,I just ran it in terminal and got this
chmod: cannot access `/dev/raw1394': No such file or directory
oh dear!
btw that looked like such an easy fix,I'm concerned I've mucked something up....

---

### Post by 73ckn797 on 2010-02-23
Here are some other things to look at:
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8121417](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8121417)

---

### Post by bumanie on 2010-02-23
To get kino going 
> sudo apt-get install kino> sudo apt-get install dvgrab> sudo apt-get install libraw1394-11> sudo apt-get install libraw1394-dev 
Have never been able to capture video as normal user user, always have had to do so as root.
To capture video > sudo kino
Hope that gets you up and going - kino works very well once all the above is installed, however, make sure you have a lot of space in /home as some files can get quite big.
Just realized you are using jaunty - I think for jaunty it is libraw1394-8 at [COLOR="Red"]step 3[/COLOR] (from memory)

---

### Post by MisFitt on 2010-02-23
Looks really good,thanks BUT
Couldn't find package libraw1394-11
-whoops!
HELP!!!!!!!!!!
edit:does it look like I could have messed something IMPORTANT up at around 2am last night?
I ran this in terminal &
computer@computer-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
computer@computer-desktop:~$

---

### Post by bumanie on 2010-02-24
I put a note down the bottom that on jaunty, I think the file [COLOR="Red"]you need is libraw1394-8[/COLOR] at step 3; not libraw1394-11, the libraw1394-11 works on karmic. At least I think it is libraw1394-8 for jaunty, I am going memory regarding that.

---

### Post by 73ckn797 on 2010-02-24
> **MisFitt said:**
> Looks really good,thanks BUT
Couldn't find package libraw1394-11
-whoops!
HELP!!!!!!!!!!
edit:does it look like I could have messed something IMPORTANT up at around 2am last night?
I ran this in terminal &
computer@computer-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
computer@computer-desktop:~$
Did you "sudo" the command?

---

### Post by MisFitt on 2010-02-24
Thanks,no,it appears not,oops
-however now that I have I am getting nowhere which is frustrating seeing a couple of weeks back the same issue with Karmic resolved very quickly and cleanly.

SOLVED;this is what I did thanks to
                     Originally Posted by **73ckn797**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8871841#post8871841")                 
                 [I]See if this will help:
[http://adventuresinswitching.blogspo...ot-loaded.html]("http://adventuresinswitching.blogspot.com/2008/04/kino-raw1394-kernel-module-not-loaded.html")
It worked like a charm just now and I have Kino'd video to prove it(to myself).
Those commands WORK!Didn't half an hour earlier so go figure.....
I'm just so grateful
[/I]

---

