---
title: "Running an application"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by rostok83 on 2009-09-20
Hello everybody!
 
I am an absolutely new user of ubuntu and i have probably a stupid problem, which i could not solve.
 
I cannot run an application from the console.
More particular, i have some ELF files, all simple application written in C.
They all are working fine from other computer (university computer), but i cannot run them not from my console and using the GUI.
 
I am in the correct folder (ls shows me those files), i type the file name i want to run and the answer i get is "bash: ntsc: command not found" (ntsc is one of the applications I tried to run), while it works perfectly in the university computer.
 
I would really appreciate help about this issue.
 
Tnx.

---

### Post by TheStroj on 2009-09-20
to run a file, you must type ./filename
=)

---

### Post by callumacrae on 2009-09-20
Try typing 'sudo [application name]' without the quotes. Works for me.

~Callum

---

### Post by pyroclastic on 2009-09-20
> **rostok83 said:**
> Hello everybody!
 
I am an absolutely new user of ubuntu and i have probably a stupid problem, which i could not solve.
 
I cannot run an application from the console.
More particular, i have some ELF files, all simple application written in C.
They all are working fine from other computer (university computer), but i cannot run them not from my console and using the GUI.
 
I am in the correct folder (ls shows me those files), i type the file name i want to run and the answer i get is "bash: ntsc: command not found" (ntsc is one of the applications I tried to run), while it works perfectly in the university computer.
 
I would really appreciate help about this issue.
 
Tnx.


if u are in the same map where the file is, u can do what  the other guy says:lolflag:

---

### Post by rostok83 on 2009-09-20
Thans for the really fast reply!!! :-)
 
But is there some way to configure it not to use ./"filename" ?
It does work on the university ubuntu...

---

### Post by cholericfun on 2009-09-20
export $PATH="/home/user/path_to_your_file"

should work

then you can type it as any other command

---

### Post by rostok83 on 2009-09-20
Tnx cholericfun, but still it is local solution for a single folder. I'm talking about the ability to run an application without "./" if i am in it's folder in the console. Some way similar to how DOS works.

---

### Post by Joeb454 on 2009-09-20
> **rostok83 said:**
> Tnx cholericfun, but still it is local solution for a single folder. I'm talking about the ability to run an application without "./" if i am in it's folder in the console. Some way similar to how DOS works.

That would involve running something like ```
export PATH=$PATH:.
``` though I think that would need to be run every time you login, or added to ~/.bashrc to be made permanent (though I wouldn't recommend that too much).

---

### Post by rostok83 on 2009-09-20
JoeB454: Exactly what i was looking for!!!
Thanks a lot to everyone who answered!!!

---

### Post by Joeb454 on 2009-09-20
Awesome :D Don't forget you can mark threads as solved again now (it's thread tools at the top of the page)

Also - if you *do* add it to ~/.bashrc - don't forget to add it at the end :p

---

