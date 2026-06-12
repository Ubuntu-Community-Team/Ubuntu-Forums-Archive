---
title: "DVD burn failures"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by OpaAussie on 2009-08-01
I have just bitten the bullet and done a complete install of 9.04 wiping XP.  Tried to burn data to a DVD, first time Brasero seemed to do a burn then got stuck on a page saying that there was x time to go till finished, I hit cancel at 6+ hours and appear to have got a valid DVD.  Next time, same data, same flavour DVD, all finished in less than 1 hour with a message - burn failed (and it had).

How to determine if software problem or hardware?

AMD Sempron 1.5 GHz, Gigabyte 7VM400M-RZ motherboard, 512 MB RAM, 80.01 GB HDD with only Ubuntu 9.04 (73.0 GB free) LiteOn DVDRW iHAP322-32 8.

Have paid for copy of Nero 9, should I try Nero for Linux?

Being pointed in right direction would be appreciated.

OpaAussie

---

### Post by Liolikas on 2009-08-01
Try **K3B** and other free burning soft for Linux do not waste money on Nero if all burning soft fails so it may be hardware problem.

---

### Post by Arup on 2009-08-01
In Brasero go to edit>plugin and disable normalize.

---

### Post by Shig on 2009-08-01
It could be enlightening to see what Brasero thinks is happening.

If you pop open a Terminal (Accessories -> Terminal under the Ubuntu menu) and run...
```
brasero --debug &> brasero-debug.txt
```
...then try to burn a data DVD, regardless of whether or not the disk burns properly you should be left with a brasero-debug.txt file in your home directory.

Once you have this file, please share it with us so that we can look into what is causing Brasero to hang up.

---

### Post by OpaAussie on 2009-08-01
> **Liolikas said:**
> Try **K3B** and other free burning soft for Linux do not waste money on Nero if all burning soft fails so it may be hardware problem.
Thanks for the suggestion Liolikas, do want to try another piece of software to determine if problem there or with burner.  Thanks for name of K3B.  Have already "wasted" purchase price of Nero 9 for now retired XP, so no extra to get Nero for Linux (I have been informed).  Will try K3B and let you know.
OpaAussie

---

### Post by OpaAussie on 2009-08-01
> **Arup said:**
> In Brasero go to edit>plugin and disable normalize.
Thank you Arup, will give this a go and report back.
OpaAussie

---

### Post by OpaAussie on 2009-08-01
> **Shig said:**
> It could be enlightening to see what Brasero thinks is happening.

If you pop open a Terminal (Accessories -> Terminal under the Ubuntu menu) and run...
```
brasero --debug &> brasero-debug.txt
```...then try to burn a data DVD, regardless of whether or not the disk burns properly you should be left with a brasero-debug.txt file in your home directory.

Once you have this file, please share it with us so that we can look into what is causing Brasero to hang up.
Thank you Shig.  I thought that there should be a way of finding out what Brasero thought was going wrong.  Looked for a file but being only hours old in Linux/Ubuntu was having trouble finding my way around let alone understanding what I was looking at!  Will try your suggestion and post back.
OpaAussie

---

### Post by HiImTye on 2009-08-01
> **Arup said:**
> In Brasero go to edit>plugin and disable normalize.
they should just remove the normalize plugin, it causes so many people so many problems

this is the likely culprit

---

### Post by MrWES on 2009-08-01
> **Liolikas said:**
> Try **K3B** and other free burning soft for Linux do not waste money on Nero if all burning soft fails so it may be hardware problem.

+1 for K3B -- well worth carrying the extra KDE libraries. Solid and reliable burning software. The only other technique I use is command line burning of iso files -- that's very reliable too.

```
growisofs -dvd-compat -Z /dev/dvd=dvd.iso && eject /dev/dvd
```


~Bill

---

### Post by OpaAussie on 2009-08-02
> **OpaAussie said:**
> Thank you Shig.  I thought that there should be a way of finding out what Brasero thought was going wrong.  Looked for a file but being only hours old in Linux/Ubuntu was having trouble finding my way around let alone understanding what I was looking at!  Will try your suggestion and post back.
OpaAussie
Have followed your suggestion and the debug file is attached
OpaAussie

---

### Post by stinger30au on 2009-08-02
> **OpaAussie said:**
> 

Have paid for copy of Nero 9, should I try Nero for Linux?

Being pointed in right direction would be appreciated.

OpaAussie

dont bother with nero linux

its an insult to linux users and its comparable to nero 3 for windows from about 10 years ago

when "ahead" decide to grow up and release a version that is at least comparable to nero 6, then install it, untill then, there is some many foss s/ws that kicks its butt its not funny

---

### Post by OpaAussie on 2009-08-03
> **Arup said:**
> In Brasero go to edit>plugin and disable normalize.

Arup and HiImTye, disabled "normalize" and tried another burn.  After a couple of hours I hit "Cancel" and out popped a DVD without an error message.  Tested the DVD and all the files seem to be accessible.  Heading in the right direction but not quite as it should be.
OpaAussie

---

### Post by Jerry N on 2009-08-03
Unless Nero has changed it's policies, you will have to pay extra for Nero for Linux - at least I did.  

I definitely prefer NeroLinux to the Linux CD/DVD burning programs, even though I had to pay for it.  That of course violates the Linux credo of "don't pay for nothin'".  K3B works good too.

Jerry

---

### Post by Pierrot Lafouine on 2009-08-10
Hi
About k3b, is there a way to get the 'growisofs' command line it generates to burn DVD ?

Thanks

---

### Post by pcjunkie on 2009-11-09
Normalize is pain in the ....
I have been googleing this for some time.
It worked fine then it just stopped working.

Normalize was the fix - all good now.

---

