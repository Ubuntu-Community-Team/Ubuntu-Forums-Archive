---
title: "brasero problem"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by jody friesen on 2009-03-28
I've been using ubuntu for about 2 weeks, and I really like it. The problem is I don't understand a few things. All I need is something to burn dvd movies. Brasero doesn't work for me and from what I have read there is no solution(I've got the newest version). I've heard about Devede and K3B but it is all so complicated for a beginner. eg. what is terminal? what are dependencies? etc. If anyone knows a good program and a simple way to install it I would really appreciate it!!

---

### Post by tombom62 on 2009-03-28
> **jody friesen said:**
> I've been using ubuntu for about 2 weeks, and I really like it. The problem is I don't understand a few things. All I need is something to burn dvd movies. Brasero doesn't work for me and from what I have read there is no solution(I've got the newest version). I've heard about Devede and K3B but it is all so complicated for a beginner. eg. what is terminal? what are dependencies? etc. If anyone knows a good program and a simple way to install it I would really appreciate it!!

Dependencies are, in short, little bits of software thatt are there to let other larger bits of software run.  Someone might come in here are correct me, but the way I see it, from a n00b(ish) stand point, that's it.

Terminal is a text based shell for entering commands that help your computer.  It may sound weird to use a shell in the modern age on a computer, but you will see, it works very well.  To open you're terminal, go to Applications > Accessories > Terminal.  See for yourself, it may look confusing, but don't worry.

The best way to install in debian and ubuntu is with aptitude. (some people might hate me for saying that but really)  to install something, go to a terminal and type 
> sudo aptitude install blahblahblah
and replace blahblablah with what you want to insrtall.  otherwise, go to the site and see how they recommend you install it.  k3b, I LOVE tat app.
in terminal:
> sudo aptitude install k3b

please tell me if I was of any help.

thanks,
tombom:popcorn:

---

### Post by jody friesen on 2009-03-28
I tried to install k3b with aptitude like you said but my computer said "this aptitude does not have super cow powers". No idea what that means???

---

### Post by Chemical Imbalance on 2009-03-28
sudo apt-get install k3b

edit: just forget this:
apt-get is preferred over aptitude

---

### Post by tombom62 on 2009-03-28
> **Chemical Imbalance said:**
> sudo apt-get install k3b


apt-get is preferred over aptitude
not by me lol.
Aptitude manages packages better, is faster, and has a gui.  If it doesn't work though, use apt-get.  you shouldn't notice too mcuh of a difference for a beginner.
Glad I could help.  Linux is great, but it can be scary when you try to dive into it.:)

thanks,
tombom:popcorn:

---

### Post by jody friesen on 2009-03-29
so I installed k3b, but it doesn't work. It says I don't have all the necessary files. The help button on my k3b doesn't work? Do I need a program like devede as well?

---

