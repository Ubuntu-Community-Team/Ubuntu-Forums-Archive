---
title: "Strange messages after shutdown..."
date: 2009-03-05
forum: New to Ubuntu
---

### Post by longtom on 2009-03-05
Hi,

I get some strange messages after shutdown:

```

acpid: exitig

[1301.536017] CIFS VFS: server not responding
[1303.536053] CIFS VFS: No response for cmd 50 mid 95

...

```

and so on....

I have to shut down the PC the hard way (pressing the main switch for a couple of seconds).

Where might that come from and is there a way I can get rid of that?

If it helps, I have edited the fstab a little while ago to share some network folders permanently.  That works fine.  Here is what I added:

```

...
#permanent mounts of shared folders :
//CHEETAH/Cheetah  /media/cheetah  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//Tiger/TIGER /media/tiger  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//Crocodile/crocs /media/crocs  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//Crocodile/Birdies /media/birds  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//sublimation/Archive /media/archive  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//Crocodile/snakes /media/snakes  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
...

```

This is the only thing I can think of I have done to induce such a reaction.

But then again this might be a bug nobody has really figured out yet.

Any suggestions welcome.

longtom

---

### Post by mikechant on 2009-03-05
I think you need to read this post:
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

My understnading of it is that the problem is due to the cifs process being killed as part of the shutdown process which then tries to unmount the cifs folders, but can't because the cifs process is gone.
It's a long running problem which has not been properly resolved due to two groups of developers wrangling about who is responsible for fixing it.
However, it looks as if most people have managed to get it to work by adding extra scripting in the shutdown process to unmount the cifs folders before cifs is terminated.

---

### Post by theozzlives on 2009-03-05
I had the same problem, here's your answer:
[http://ubuntuforums.org/showthread.php?t=293513]("http://ubuntuforums.org/showthread.php?t=293513")

---

### Post by longtom on 2009-03-06
First of all thank you to you and theozzlives for the link.  It solved my problem.

> **mikechant said:**
> I think you need to read this post:
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

It's a long running problem which has not been properly resolved due to two groups of developers wrangling about who is responsible for fixing it.
However, it looks as if most people have managed to get it to work by adding extra scripting in the shutdown process to unmount the cifs folders before cifs is terminated.

Now - that is really sad.  I was kind of hoping Ubuntu (or linux in general)  would be free of that kind of haggling.  Naive - of course - but reading up on the high moral ground linux developpers would like to see themselves, I was kind of hoping things like that can be resolved in a more....harmonic manner.

But the more I read about linux the more I become aware of the infighting - sometimes in a severe and somewhat uncivilised manner...to put it mildly.

Linux, Ubuntu or there not....it's only people I guess,....still...

longtom

---

