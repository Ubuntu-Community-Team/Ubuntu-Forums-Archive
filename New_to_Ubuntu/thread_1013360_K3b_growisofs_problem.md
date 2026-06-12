---
title: "K3b growisofs problem"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by simontaylor on 2008-12-16
Hi ubuntusers,

have posted previously re similar issue - that time it was the upgrade to Hardy Heron which nixed my ability to copy CDs and DVDs - this time, with Ibex installed, I can indeed copy CDs, however not DVDs. I get this:

> growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
:-( unable to O_EXCL /dev/scd0: someone was in time to remount?

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray

which is to say: 

1) the DVD reads fine; 

2) 'eject' usually requires a little help (something odd about this, have noted it also with CDs as a general problem); 

3) on inserting blank disc of requisite layers and size, the preceding note; 

4) have tried three blank discs in a row to no avail; 

5) have managed to save raw iso on my harddrive of the DVD I was copying but cannot get it onto disc!

Help would be appreciated. 

Thanks, 
Simon

---

### Post by Shhnap on 2008-12-17
Ok a few suggestions:

1) Make sure you have added the Medibuntu repositoty. ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) read this to find out how)

2) Why are you using growisofs to copy DVD's, because, if it does not really matter what copies it, why not use Brasero?

---

### Post by simontaylor on 2008-12-18
cheers Shhnap,
my experience with Brasero was that compared to K3b it sucked. What I was trying to get at was an interpretation of the debugging report. I don't understand what K3b means when it reports:

> Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
unable to O_EXCL /dev/scd0: someone was in time to remount?

curiously, I have been able to move the iso onto a DVD - at 2.4x ... and in the process managed to salvage an earlier project which I'd assumed aborted and lost.

But thanks for the medibuntu tip. I have updated. I was missing some codecs. Will see if this makes a difference when the next project comes up.

In the meantime, can anybody interpret my K3b debugging report?

Best,
Simon

---

