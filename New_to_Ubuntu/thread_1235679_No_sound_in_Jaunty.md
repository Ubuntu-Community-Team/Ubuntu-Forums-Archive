---
title: "No sound in Jaunty"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Tmatherne on 2009-08-09
Hi, all, 

I am running the latest UNR, and checked for compatibility before installing.  I am running on a HP Mini 1000 series.  The Ubuntu page says that there is little known issue with the system, it should just install and go.  However, I installed and have no sound.

This is beyond my ability to fix apparently (have been trying for 2 days=]).  Any ideas?

Thanks.
Tommie

---

### Post by fooman on 2009-08-09
open a terminal and run this command:

```
sudo m-a a-i alsa-source
```if that does not fix it...consider installing the hp-mini-remix from forum member [aysiu]("http://ubuntuforums.org/member.php?u=21941").  
here is the link:

[http://psychocats.net/hpminiremix/download/](http://psychocats.net/hpminiremix/download/)

i am using that on my hp 1035nr and it runs perfectly.  sound, video, wireless, everything working right out of the box!  :)

---

### Post by Tmatherne on 2009-08-09
Trying your terminal code suggestion, I get the response of:
 
sudo m-a a-i alsa-source
Did you give me a typo? Or am I just SOL and have to reinstall (I'd really rather not=]).
 
Will if I have to, though.
 
Thanks,
 
Tommie
 
EDIT:  Wow, that copy and paste didn't work at ALL, did it?  The error code I was getting said that "m-a" is not a valid command.

---

### Post by Commisar Jimp on 2009-08-09
I know how you feel, I had sound problems too, if you haven't already you might want to look at this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449). It's got a lot of information, but sound problems can be just about impossible to fix. I ended up reinstalling after working on it with no success for about three days.:(

---

### Post by Tmatherne on 2009-08-10
OK, now I am truly confused!  The problem is SOLVED....sorta?
 
Following Jimp's advice (thanks, BTW), I went through the thread about sound issues.  Still no sound...unless I plug in headphones.  Apparently, the sound card is working, but only the output that goes to an external source.  The internal speakers still give me bupkiss.
 
One thing that I do notice when I run AlsaMixer, though.  There was mention in the original thread about green boxes mean the sound is on, grey boxes below the mixer bar mean muted.  There is one setting (PCM) with no box below it at all.  Could this be the problem?  And if so, any suggestions on fixing it?
 
Thanks for everything so far.
Tommie

---

