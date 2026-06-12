---
title: "danger from the deep"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by ubudog on 2010-06-26
Please help!  :confused:  I downloaded the dangerdeep svn, no problems.   How do I compile it?  Thanks.

---

### Post by da burger on 2010-06-26
How did you download it? I'm looking at the download page of their site now and I can see 4 ways to get it immediately. Each will have a different method of install so please tell us which you have.

---

### Post by Zeike on 2010-06-26
He clearly said he retrieved it from svn...


Right on the downloads page it gives you instructions for compilation:
> We use the build system scons, so to compile a debug version try the command:

scons debug=1 datadir=/path/to/cvs/dangerdeep/data

You might have to install the scons package first.

---

### Post by da burger on 2010-06-26
Whoops sorry. Must read these things more carefully...

Yep that's the command you want.

---

### Post by ubudog on 2010-06-26
> **Zeike said:**
> He clearly said he retrieved it from svn...


Right on the downloads page it gives you instructions for compilation:


You might have to install the scons package first.

Thanks, but when I do that, I get this.  (Oh, and I did use the actual file, not /path/to/cvs/dangerdeep/data/)  


```
scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 858, in _main

```  :confused:

---

### Post by ubudog on 2010-06-26
Looks like I got that figured out.  Scons is a little new to me.  I will let you know if I need any more help.  Thanks guys! :guitar:

---

### Post by auspot on 2012-06-28
can someone help me with this problem?

bill@bill-ET1831:~$ svn co [https://dangerdeep.svn.sourceforge.net/svnroot/dangerdeep/trunk/dangerdeep/](https://dangerdeep.svn.sourceforge.net/svnroot/dangerdeep/trunk/dangerdeep/) dangerdeep
svn: Working copy 'dangerdeep' locked

Thanks
auspot

---

### Post by overdrank on 2012-06-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

