---
title: "Failed to execute child process &quot;vlc&quot; (No such file or directory)"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Cesaar on 2009-07-06
I followed the steps [[COLOR="Blue"]in this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=613023&page=2&table#post3778055") and broke the vlc player. :( 
I get this message when trying to run from Sound & Video>VLC media player:

[IMG]http://herebemudkips.googlepages.com/Screenshot-Error.png[/IMG]

and when I try to run from Terminal I get this one:
```
cesar@cesar-laptop:~$ vlc
bash: /usr/bin/vlc: No such file or directory

```

I have tried: 
```
sudo apt-get purge vlc
sudo apt-get install vlc
```
more than once to no avail.

What can I do?



---UPDATE---(jul 6, 15:54)
I also tried the following commands:```
cesar@cesar-laptop:~$ cvlc
cesar@cesar-laptop:~$ qvlc
cesar@cesar-laptop:~$ svlc
``` and all of them "replied":
```
exec: 2: /usr/bin/vlc: not found
```
However, the following actually displays the man page
```
cesar@cesar-laptop:~$ man vlc
```

---

### Post by ecmatter on 2009-07-06
Did you follow the advice from later in that thread to reinstall wxvlc?

---

### Post by Cesaar on 2009-07-06
> **ecmatter said:**
> Did you follow the advice from later in that thread to reinstall wxvlc?
```
cesar@cesar-laptop:~$ sudo apt-get install wxvlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wxvlc

``` :/

---

### Post by Cesaar on 2009-07-06
OK Problem FIXED!

I noticed that every time I apt-get remove'd and apt-get install'ed vlc, the apt-get utility wouldn't re-download vlc. I noticed then that it would instead use the file /var/cache/apt/archives/vlc_0.9.9a-2ubuntu1_i386.deb to install. I deleted that file and reinstalled vlc. No problems now!!

---

