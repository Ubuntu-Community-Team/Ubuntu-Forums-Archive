---
title: "after renaming root account i am not able to access it"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by anshul_nit on 2009-04-18
i am using ubuntu ultimate version and i had renamed the root account..
e.g. by "asd" using the command - # usermod -l asd root 
successfully root account had been renamed by asd but i am neither able to access new account "asd" nor original accont "root".
when i use sudo su in the command line it says-"no passwd entry for root!"
and also not able to change the new account password..i tried for command # passwd asd
but it says "You may not view or modify password information for asd".
Moreover when i use gksudo it says user root doesn't exist.
Could i able to get root previleges..!!:(
your reply will be highly appreciated 
thanks..

---

### Post by Don1500 on 2009-04-18
two words......re - install.

When you tell the Dr.: "It hurts when I do this." He will tell you: "Don't do that."

---

### Post by anshul_nit on 2009-04-18
thanks for the reply..
Is there no other way than reinstall..

---

### Post by amingv on 2009-04-18
I'd try and boot from a livecd, then modify "asd" back to "root" in the passwd file. (after making a backup, of course) I'm not sure if it'll work but what else have you got to loose?
EDIT:
/ect/passwd, that is.
EDIT2:
In the livecd it won't be there, though, it will be somewhere in /media after you mount your hard disk. Just added this because I believed the clarification had to be made.

---

### Post by anshul_nit on 2009-04-18
i also tried to run in single user booting mode but it also doesn't work..is there another method to change the password b/c i hav installed many things on the system

---

### Post by Vunutus on 2009-04-18
First off, don't rename root. Just don't do it.

Second, I'm not an expert in this area but you might try editing /etc/passwd (which needs root permissions ironically but I assume you can still sudo it). The first line in that file should be the root account (or what is in place of it now). If anything looks odd there (like if it's still called root, or inconsistent or something) then post it here.

---

### Post by anshul_nit on 2009-04-18
thank u for your valuable suggestion..it worked using live cd
but using command line it didn't worked!!!
i did use # gksudo nautilus 
and successfully edited the passwd file, i just replaced the "asd" by "root".
thanx..amingv 
Regards..

---

### Post by anshul_nit on 2009-04-18
@ Vunutus
thanx for the reply..

---

### Post by juancarlospaco on 2009-04-18
By the way, by default only Users with existing */home/myusername* can Login i think...

---

### Post by amingv on 2009-04-18
> **anshul_nit said:**
> thank u for your valuable suggestion..it worked using live cd
but using command line it didn't worked!!!
i did use # gksudo nautilus 
and successfully edited the passwd file, i just replaced the "asd" by "root".
thanx..amingv 
Regards..

I'm glad it worked. :)
Just think more carefully the next time you tinker, OK?

---

### Post by swoll1980 on 2009-04-18
> **amingv said:**
> I'm glad it worked. :)
Just think more carefully the next time you tinker, OK?

Why? If he doesn't break it, he won't be able to fix it.

---

### Post by amingv on 2009-04-18
> **swoll1980 said:**
> Why? If he doesn't break it, he won't be able to fix it.

Analysing what we do before we do it brings both anticipation and solution to a problem. There's an universal rule to that: Think before you type. After all, he was just an inch from reinstalling Ubuntu without leaning a thing.

But I can't say I disagree with you either, I mean, now even I know a solution if I find such a problem in the future (I wasn't sure of the solution I posted), so I guess I should rephrase what I said to "Break it, but break it more carefully..." :)

---

### Post by nandemonai on 2009-04-18
Why rename root? By default the root user isn't even enabled in Ubuntu. :-k

---

