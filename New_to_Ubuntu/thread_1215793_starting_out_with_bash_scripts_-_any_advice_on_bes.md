---
title: "starting out with bash scripts - any advice on best practices?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by bennychidge on 2009-07-17
please excuse my knowledge here.

I am new to Ubuntu and have setup a VPS and am slowly learning lots of great things about Ubuntu. Now I am having a little look at bash scripts and thats pretty good stuff to.

here is a script I am going to implement onto my vps

[http://www.askapache.com/javascript/serve-external-javascript-files-locally-for-increased-speed.html]("http://www.askapache.com/javascript/serve-external-javascript-files-locally-for-increased-speed.html")

A few questions I have are

What is the reference in the script to ```
$HOME
``` and ```
$OLDPWD
```

are these hard wired onto a Ubuntu system, how do I find out there locations? (```
$HOME
```) seems to be a reference to the root folder.

Also what is the best practice? Should I download the ga.js and store it where? somewhere in root and add a symbolic link to my script folder within my website. Or should I save it straight to the script folder and not bother sym linking it?

Also do you have any great examples/tutorials for writing understanding how to write bash scripts?

Thanks in advance and I appologise if these are silly questions.

---

### Post by Tibuda on 2009-07-17
$HOME is the current user home directory, usually in /home/$USER ($USER is the current user name).
$OLDPWD is the last directory you were in. It changes everytime you "cd" to different dir. Try playing with them in a terminal:
```
echo $HOME
cd /home
echo $OLDPWD
cd $HOME
echo $OLDPWD
```

---

### Post by lavinog on 2009-07-17
> **bennychidge said:**
> 
Also do you have any great examples/tutorials for writing understanding how to write bash scripts?

Thanks in advance and I appologise if these are silly questions.
There are no silly questions

I find the advanced bash scripting guide to be a good resource for learning bash: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by Dill on 2009-07-17
To answer your question about tutorials, one of the best tutorials is probably one by the Linux Documentation Project:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

You may find other, shorter tutorials easier to digest as you begin bash scripting; I would start out Googling "bash scripting" and find a few beginners tutorials to whet your appetite. Then, as you feel more comfortable in the shell, move on to the above tutorial and rock and roll.

Cheers,
Dill

---

### Post by Cheesemill on 2009-07-17
It may take longer to write but **document your code with comments (# )!!!**
 
When your looking at scripts that you wrote over a year ago it makes life a hell of a lot easier :)

---

### Post by lavinog on 2009-07-17
> **Cheesemill said:**
> It may take longer to write but **document your code with comments (# )!!!**
 
When your looking at scripts that you wrote over a year ago it makes life a hell of a lot easier :)

Yes, and space it out so it is readable. Use indentation for blocks of code like for and while loops.

---

