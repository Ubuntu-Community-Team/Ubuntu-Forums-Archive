---
title: "print problems with abiword"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by plankenstein on 2009-03-27
Last night my wife opened a ms word document in abiword and made a few changes, then saved it in abiword format.  But when she tried to print it, she got a "write error 32".  Tried the diagnose thing but got nowhere with that.  We normally use open office, so i tried opening it in that and it prints but the formatting is all messed up.  This is her resume, so I have got to fix this problem or she'll start pushing me to go back to micro-junk and I don't want to do that.  I didn't think to try printing anything else in abi so it might just be something to do with that one document.  I'll try that when I get home this evening.  In the mean time, any help, sugestions, or thoughts would be greatly appreciated.

Thanks is advance

---

### Post by plankenstein on 2009-03-28
Okay, quick update on the print problem.  Went home and tried to print a new document in abiword and it worked.  So I decided to try the wife's resume again and it printed too.  But, if I make any changes to any document in abiword and save it, I have to close abiword and then reopen it before I can print. Otherwise I get the same error again. Anybody have any ideas?

---

### Post by lykwydchykyn on 2009-03-28
> **plankenstein said:**
> Okay, quick update on the print problem.  Went home and tried to print a new document in abiword and it worked.  So I decided to try the wife's resume again and it printed too.  But, if I make any changes to any document in abiword and save it, I have to close abiword and then reopen it before I can print. Otherwise I get the same error again. Anybody have any ideas?

Are you saving it in microsoft format or abiword format?

---

### Post by plankenstein on 2009-03-28
sorry for the delay, I've been out and about today.  All of these documents have been saved in abiword format.

Any thoughts?

---

### Post by lykwydchykyn on 2009-03-29
Try two things for the sake of diagnostic info:
 - run abiword from the terminal like this:
```

abiword &>abiword.log

```
Try to reproduce the error.  If you do, see if there are any detailed error messages in abiword.log.  If so, post them here.

 - Check /var/log/cups/error_log for error messages occurring at the time you get the print errors.  Post them here.

I cannot find a reference to a write error 32, so more detailed info is necessary.

---

### Post by plankenstein on 2009-03-29
Okay, I started abiword from the terminal and it failed again. The output from the error log is as follows:

E [29/Mar/2009:22:19:06 -0500] [Job 72] pstocanonij write error,32.
E [29/Mar/2009:22:19:06 -0500] PID 6296 (/usr/lib/cups/filter/pstocanonij) stopped with status 1!
E [29/Mar/2009:22:19:06 -0500] [Job 72] Job stopped due to filter errors.

There was more that followed, but it looked like information and data.  Nothing about any errors listed in that part of it.

If it helps any I'm running a canon ip2600 printer using a driver I loaded from canon-asia. This error log gives me the feeling that it may have something to do with that, but everything else prints fine? 

I'm at a loss.:confused:

---

