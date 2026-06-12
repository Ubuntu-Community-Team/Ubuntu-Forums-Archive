---
title: "Problems with natty upgrade"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by charlier653 on 2011-07-08
Made the mistake of upgrading to Natty. Upgrade manager popped up today with the message that I had an incomplete upgrade, and wanted me to add more to finish. Now all I get is several loading <app name> [ok], and then it hangs. Have tried many different things from this forum, but no joy. I can get to tty1 for a command line. I have tried ```
startx
``` and all I get is an error message <could not start gnome>.

I have no way that I know of to reinstall the video driver if that is the problem. The computer will not even let me into recovery mode, without dropping back to tty1 (I assume this is what is meant by shell).

I have tried to make sense of the Xorg.0.log file, essentially it's telling me that it is trying to load the proper files, but then quits.

Attempting previous versions gets me a messed up purple screen.

When I try to use low graphics mode I get the error
```
Your screen, Graphics card, and input devices could not be detected correctly.
You will need to configure these yourself
```

I have no idea how to do this.

Can someone point me to a guide of some sort that can help me with this?

---

### Post by carverj on 2011-07-08
When upgrading to new version I always backup my user data and then install Ubuntu from CD.
Have you backed up user data in case the system requires a re-install?
Also, jayekayser posted that he fixed same issue so perhaps this will lead you in the right direction: -
[http://ubuntuforums.org/showthread.php?t=1049386](http://ubuntuforums.org/showthread.php?t=1049386)

---

### Post by charlier653 on 2011-07-08
I have looked at that thread. I looks like similar issue, on 10.04.

However, he had more functionality available to him than I currently do.

Normally, I put my /home folder on a separate physical drive, after having had several old drives die. Let's hope I did that when I installed 10.04.  

The only reason I accepted the upgrades is I had read somewhere that certain programs I use had upgrades that could only be used on
11.04. This is my own fault, I didn't check his sources. At this point I am doubting his story.

In short, it looks like I will be doing a complete reinstall. I've downloaded the live cd, and am about to give that a whirl.


EDIT:

For some reason, I didn't set /home on a separate drive. 

Was going to resize and combine a couple of partitions, but for some unknown reason gparted can't do anything with ANY partitions on my box. I am not able to resize, move, copy or anything.

---

