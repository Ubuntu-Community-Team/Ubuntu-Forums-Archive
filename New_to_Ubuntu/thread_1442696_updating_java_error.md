---
title: "updating java error"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by myotis on 2010-03-30
I have updated java (as required to run jgr) but  get the following error

graham@T42-linux:~$ sudo update-java-alternatives -s java-6-sun
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.

I realise this has something to do with firefox (at least I think it does) but not sure how to fix it, nor am I sure of the consequences of ignoring it.

Can someone help?

Thanks,

Graham

---

### Post by myotis on 2010-03-30
I  wonder a little bit if its worth the bother, so can anyone help me with the commands to revert back to the default and unistall the sun version.

Thanks,

Graham

---

### Post by QIII on 2010-03-30
First thing I would do is give this a look.

Very simple instructions, but it does require the use of the CLI.

The newest version of Java in the repos is Update 13, which has some severe security flaws.  The current Java is Update 18.  Canonical has decided to use OpenJDK, which is well and good.  But it still has some maturation to go.  The OpenJDK community is diligently working on it.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by myotis on 2010-03-30
> **QIII said:**
> First thing I would do is give this a look.



Thanks, I will give this a look, my "quick look" at JGR, which I have no plans to actually use, is getting very involved.

Graham

---

### Post by QIII on 2010-03-30
Just one of those things.

I have to use the latest version of Java for two reasons:  it is specified by clients and my personal bank website won't work without the latest version of Java.

The latter does not seem to be happy with OpenJDK, even though OpenJDK is just the open source version.  It specifically expects Java Update 18 right now.

---

### Post by myotis on 2010-03-30
Thanks again, 

Graham

---

