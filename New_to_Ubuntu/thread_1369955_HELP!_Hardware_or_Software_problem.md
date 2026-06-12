---
title: "HELP! Hardware or Software problem?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by UbuSheldon on 2010-01-01
Hi,

New to Umbutu and all good EXCEPT in  trouble with streaming video.  YouTube, BBCi player (streamed) and BBCi player (downloaded) are stuttering (horizontal cutting lines in image).   It's as if processor can't cope.  Followed 2 days of various threads to no avail.  Have run out of ideas and am lost in ubuntu speak.

AMD 64 3200+, 2GB RAM, Radeon 9200 graphics.  Running at 75% CPU with BBCi streaming and peaks to 100% if I try to do anything else at same time.  All latest updates installed. Just don't know enough about this stuff AAaaarrrrghhh

Hope some one can help, at the very least tell me if my machine needs to see a specialist!  I don't want to go back to windows but it worked there:frown:

Thanks in advance...

---

### Post by falconindy on 2010-01-01
32 or 64 bit install? If you're not sure, post the output of 'uname -a'.

---

### Post by jbrown96 on 2010-01-01
Flash on Linux is really bad. Are you running 64-bit Ubuntu? Adobe has a alpha version of flash available that dramatically improves flash performance. 

You can check if you are running 64-bit with ```
uname -m
``` x86_64 is 64-bit. 
If you are using 64-bit, then switch to 64-bit flash.

1) Remove your current Flash ```
sudo apt-get remove flashplugin-nonfree
```
2) Follow [these directions]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

---

### Post by UbuSheldon on 2010-01-01
Cheers,

I think I'm running 32bit

sheldon@sheldon:~$ uname -a
Linux sheldon 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
sheldon@sheldon:~$ uname -m
i686
sheldon@sheldon:~$ 

So do I go and get the 64 bit Adobe player?

---

### Post by falconindy on 2010-01-01
Nope. i686 is a 32 bit architecture. You can't run 64 bit software on it. I hate to say it, but its likely related to your graphics card and not your architecture.

You could try this: download, burn, and boot off the 64-bit live CD and try flash there. You'll want to make sure that you install the 64 bit alpha from adobe labs, and not the the 32 bit plugin wrapped for 64 bit.

---

### Post by UbuSheldon on 2010-01-01
Cheers, it's a direction to go in at least.  64 bit ubuntu or new graphics card here I come (he said with nervousness).

---

### Post by cenzorrll on 2010-01-01
This seems to be a problem on the flash side of things.  The forums are riddled with threads on the same issue, apparently there is no fix as of yet.

so...software problem

---

### Post by jbrown96 on 2010-01-01
This is a flash problem. There is no GPU acceleration for flash, so buying a new card will not help at all! If anything you will need a faster CPU.

Here's what I would recommend.
1) Install the 64-bit version of Ubuntu
2) Install 64-bit flash. It will be somewhat better, but even on my 2GHz Core 2 Duo, full screen flash stutters a little.

Adobe is supposed to release Flash 10.1 in "the first half of 2010," which should put all three platforms (Win, Mac, Linux) on par performance-wise (with the notable exception of GPU acceleration in Linux). This should mean dramatic performance improvements on Linux and Mac and reasonable improvements on Win.

Don't upgrade your hardware for Flash; you literally can't throw enough money (buying hardware) to solve this problem on Linux. The 64-bit version should help, but it won't be a miracle.

---

### Post by UbuSheldon on 2010-01-02
I'll be patient.  Cheers everyone.

---

