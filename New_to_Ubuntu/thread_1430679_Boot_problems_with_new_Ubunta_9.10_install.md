---
title: "Boot problems with new Ubunta 9.10 install"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by PackJac on 2010-03-15
I just installed on my C drive Ubunta 9.10 64 bit for the first time using the Windows Installer (WUBI). All seemed to go well until I rebooted. When I choose the UBUNTU option (instead of Windows 7) I get the following message: "Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else, TAB lists possible device/file completions." 

Huh? What the heck does this mean and how do I proceed from here?

I have a new ComPaq Windows 7-64 bit machine with 3 gigs of RAM and 500 MB of hard drive space. 

Can anybody help?

PackJac

---

### Post by J V on 2010-03-15
ugh, I come across this all the time... Not sure what the fix was, I think thats just a message and you should just wait for it to boot up...

---

### Post by PackJac on 2010-03-16
> **J V said:**
> ugh, I come across this all the time... Not sure what the fix was, I think thats just a message and you should just wait for it to boot up...

Personaly, I think waiting 30 minutes for it to boot is too long to sit there looking at the prompt: "sh:grub>-

PackJac

---

### Post by ubudog on 2010-03-16
> **PackJac said:**
> Personaly, I think waiting 30 minutes for it to boot is too long to sit there looking at the prompt: "sh:grub>-

PackJac

Yeah.  Boot into a recovery console (drop to root shell) and type: ```
fsck
```  :p

---

### Post by drs305 on 2010-03-16
PackJac,

Welcome to the Ubuntu forums. Take a look at this link that provides a solution to WUBI bug. Read the page and determine if this is the situation that applies to you. It is a common 9.10 bug and I don't know if a solution has been released.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

