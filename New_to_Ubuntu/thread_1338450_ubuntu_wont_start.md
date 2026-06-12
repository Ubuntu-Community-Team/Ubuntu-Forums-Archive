---
title: "ubuntu wont start"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by starstalker on 2009-11-26
Hi
I installed ubuntu using wubi 3 weeks ago and every thing was going great exept for a couple of minor problems, yesterday I was browsing the net and I was asked to update my ubuntu ofcourse I accepted and when it finished it asked me to restart 
after the restart I choose ubuntu from my boot screen and it started the GNU GRUB thingy I tried a couple of things and it doesnt work keep telling "no kernel loaded ".
 
what should I do??? ](*,)
 
 
thanks for your help .

---

### Post by lisati on 2009-11-27
Can you see more than one entry for "Ubuntu" when grub does its stuff? 
Does selecting the third or fourth allow you to use your system?

---

### Post by starstalker on 2009-11-27
Will grub doesnt do its stuff
the first screen that you can select ubuntu or windows from is there but the other one that appears after I chose ubuntu doesnt start instead it goes into grub interface (the one that is like the terminal).
 
by the way windows is working perfectly

---

### Post by lisati on 2009-11-27
> **starstalker said:**
> Will grub doesnt do its stuff
the first screen that you can select ubuntu or windows from is there but the other one that appears after I chose ubuntu doesnt start instead it goes into grub interface (the one that is like the terminal).
 
by the way windows is working perfectly

OK. Is the prompt like this:
> grub>
or is it more like this?
> username@computer-name$

---

### Post by starstalker on 2009-11-27
it is 
sh:grub>
 
here is what happens after I chose ubuntu
first screen:
Try (hd0,0) : NTFS5 : No Wubildr
Try (hd0,1) : NTFS5 :_                                  //pauses for a couple of seconds then
 
second screen:
                 GNU GRUB version 1.97~beta4
[minimal Bash-like line editing is supported. .......bla bla bla.......]
 
Sh:grub> _

---

### Post by MelDJ on 2009-11-27
try using windows to do a chkdsk /f. then shutdown cleanly, boot into windows and then boot into ubuntu

---

### Post by starstalker on 2009-11-27
> **MelDJ said:**
> try using windows to do a chkdsk /f. 
 
how can I do that?

---

### Post by MelDJ on 2009-11-27
see: [http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

chkdsk /f does not attempt repairing bad sectors, chkdsk /r does.

chkdsk /r is significantly slower than chkdsk /f

---

### Post by starstalker on 2009-11-27
ok just finished from it still the same nothing changed

---

### Post by starstalker on 2009-12-02
I will uninstall ubuntu and install it as a dual boot,not using wubi in hopes that this will solve things but I would like to still hear if this problem happend to anyone else and if there is a solution

---

