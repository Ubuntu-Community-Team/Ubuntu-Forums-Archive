---
title: "Restart does not work!"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by andy8 on 2011-02-23
Restart has stopped working :confused:
It hangs there until I manually power the PC down myself. I have searched the net but found nothing, was working fine on 64 bit but has now stopped on a 32bit install. Is there a quick fix? Andy

---

### Post by thesavager on 2011-02-23
Have you tried to reboot your computer from shell command ? just to check if its really impossible to reboot or maybe a graphical programm problem, try this :

1) ctrl+alt+F2
2)login as user
3)sudo shutdown -r now

Else try to figure out , what process is doing the hangup!
open a shell or ctrl+alt+F2
then: ps -aux

now check the whole list to see what programm is consuming all the CPU power !
kill -9 <process number>

hope this helps.

---

### Post by Rubi1200 on 2011-02-23
Try to avoid hard shutdowns or resets; they may cause file-system damage.

Instead, use this:

Hold down Alt and SysRq (which is the Print Screen key) while slowly typing R E I S U B will get you safely restarted. Alternatively, R E I S U O will do a shutdown rather than a restart.

---

### Post by andy8 on 2011-02-23
> **thesavager said:**
> Have you tried to reboot your computer from shell command ? just to check if its really impossible to reboot or maybe a graphical programm problem, try this :

1) ctrl+alt+F2
2)login as user
3)sudo shutdown -r now

Else try to figure out , what process is doing the hangup!
open a shell or ctrl+alt+F2
then: ps -aux

now check the whole list to see what programm is consuming all the CPU power !
kill -9 <process number>

hope this helps.

Thanks for the quick response. 
Tried the first  1) ctrl+alt+F2 2)login as user 3)sudo shutdown -r now, sadly it still hung there.

and ps -aux told me there was syntax error. Maybe I typed it in wrong? 
I think it might have something to do with the graphics card. I'll try taking off the additional drivers and see what happens.
If you can think of anything else I'll be grateful.
Thnks again, Andy.

---

### Post by andy8 on 2011-02-23
> **Rubi1200 said:**
> Try to avoid hard shutdowns or resets; they may cause file-system damage.

Instead, use this:

Hold down Alt and SysRq (which is the Print Screen key) while slowly typing R E I S U B will get you safely restarted. Alternatively, R E I S U O will do a shutdown rather than a restart.

Thanks tried all that and nothing helped. Thanks, Andy

---

### Post by andy8 on 2011-02-23
Well, it made no difference. It still hangs there on restart, without the graphic card drivers. Instead of all the usual unmounting weak file system[ok] etc, I get the ubuntu shut down screen and the five dots. Two turn red and then it hangs there?
This one thing has got me. Andy

---

### Post by thesavager on 2011-02-23
Wow Andy ... when you can not do an command like:  ps -aux , cos that command would let you see the processes on your computer ... then i start thinking that your cd .. you used to install Ubuntu isn't complete !!!
Did you do an MD5 check ...after downloading the ISO file ?
And burn the cd/dvd ... on the lowest speed possible.

---

### Post by andy8 on 2011-02-24
I think you are right. It must be the cd's. I used a different cd and this came up after sudo shutdown....etc
[176.119992] restarting system.s init.dbus main process killed by term signal.
just off to try ps-aux. will let you know what I find.

---

### Post by andy8 on 2011-02-24
Typed in the ps-aux and have no idea what I'm looking for. A screen comes up with, well no idea? 
Andy

---

### Post by andy8 on 2011-02-24
I'm gonna try it from the usb. See what happens then. Andy

---

### Post by andy8 on 2011-02-24
Nope, still hangs there on 32bit, will now try 64bit and then thats it! Will just leave it without restart.
Andy

---

### Post by andy8 on 2011-02-24
Works fine on 64bit! lol Have no idea why. Oh well restart works!!!!!!!!!! I'm happy. Andy

---

### Post by thesavager on 2011-02-25
Great work andy ! 
The ps -aux command may also been used without the - option ....
so try this ... ps aux  ... you should see the processes of your pc.

Have fun!

---

### Post by andy8 on 2011-02-25
Thanks, I will. Loving ubuntu takes less than a hour to start again from fresh when it all goes wrong. I keep a pen drive handy now and keep all the web pages that help me fix the problems/fixes/changes I can do on that. Vista from fresh takes a day to do just the updates! Thanks again. Andy

---

