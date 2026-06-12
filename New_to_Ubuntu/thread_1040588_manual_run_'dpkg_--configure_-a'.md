---
title: "manual run 'dpkg --configure -a'"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by mrbfrog on 2009-01-15
I try to update my system and I get this message.  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I dont know how to do this.
thank you

---

### Post by kansasnoob on 2009-01-15
In terminal run:

```
sudo dpkg --configure -a
```

---

### Post by Shazaam on 2009-01-15
Applications>Accessories>Terminal. After it opens enter the code, It will ask you for your USER (login) password. As you enter it you wont see it print but that is ok. Just enter your password then hit your ENTER key.

---

### Post by santanas on 2009-01-15
thanks for that that really help me out ....

---

### Post by sisco311 on 2009-01-15
open a terminal (Applications -> Accessories -> Terminal)
and type(or copy paste):
```
sudo dpkg --configure -a
```
then press enter. 

you will be asked for your password. type it and press enter again.
(there is no visual feedback when you type your password)

edit:
d'oh. i'm slow. :)

---

### Post by Antonio Lo Nardo on 2009-01-20
Could someone modify that message adding "with administrator privileges" ?

---

### Post by gbinman on 2009-01-20
Thanks,

I just started with ubuntu.  I have done a number of installs... first with a spare hard drive in place... several versions there.  And then using wubi to add ubuntu to 4 windows machines.  

My notebook lost power in the middle of the first update (221 updates) to 8.10.  When it came back, the error with the suggestion to run dpkg was there.

I was pleased to find the exact issue here.  Its still running on the notebook.  It is displaying pages of messages.  With 221 items to process, I figure it will be at it a while.

I am using the remote desktop feature to run and monitor its progress.  It was fun to find the VNC derivative packaged.  I used to use it extensively to support networks (used to have a networking business).

Anyway I really appreciate finding the answer so easily.  Thanks

---

### Post by hyper_ch on 2009-01-20
> **Antonio Lo Nardo said:**
> Could someone modify that message adding "with administrator privileges" ?
why?

---

