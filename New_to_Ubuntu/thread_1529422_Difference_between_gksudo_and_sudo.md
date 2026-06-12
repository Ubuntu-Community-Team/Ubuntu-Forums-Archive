---
title: "Difference between gksudo and sudo?"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Mariane on 2010-07-12
When should I use gksudo and when should I use sudo?

Mariane

---

### Post by ST3ALTHPSYCH0 on 2010-07-12
gksudo is for graphical applications
sudo is for command line applications

---

### Post by audiomick on 2010-07-12
Hi.
gksu or gksudo is for starting graphical applications.
Have a look here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by philinux on 2010-07-12
> **Mariane said:**
> When should I use gksudo and when should I use sudo?

Mariane

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by audiomick on 2010-07-12
> **philinux said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
beat you to it... :)

---

### Post by diablo75 on 2010-07-12
Here's a question I have about this question:

Why was it necessary to create gksudo in the first place?  I just don't understand why some people get up in arms when I tell them "I just typed sudo gedit" or something and they're like, "No no, you did it wrong.  Type gksudo gedit"... despite the fact that, as far as I can tell (in this example anyway) they do the exact same thing.

I know that technically they don't do they exact same thing but I'm not really keen on the details so that's what I was curious about.  Was it not possible to make the sudo command a little more... "smart" in its versatility?  In other words, couldn't they have made it able to detect whether you are trying to start a GUI-based program vs. a CLI-based program so you wouldn't have to worry about typing gksudo in the first place?

---

### Post by audiomick on 2010-07-12
> **diablo75 said:**
> Here's a question I have about this question:

Why was it necessary to create gksudo in the first place?

That is in the link that Phil and I posted.

> 
  Was it not possible to make the sudo command a little more... "smart" in its versatility?

I think that is exactly what happened, and gksu is the result.

Maybe I am wrong, but I think that gksu or gksudo is always "safe", i.e could be used all the time. Does anyone know anything to the contrary?

---

### Post by sisco311 on 2010-07-12
> **diablo75 said:**
> Here's a question I have about this question:

Why was it necessary to create gksudo in the first place?  I just don't understand why some people get up in arms when I tell them "I just typed sudo gedit" or something and they're like, "No no, you did it wrong.  Type gksudo gedit"... despite the fact that, as far as I can tell (in this example anyway) they do the exact same thing.

I know that technically they don't do they exact same thing but I'm not really keen on the details so that's what I was curious about.  Was it not possible to make the sudo command a little more... "smart" in its versatility?  In other words, couldn't they have made it able to detect whether you are trying to start a GUI-based program vs. a CLI-based program so you wouldn't have to worry about typing gksudo in the first place?

By default, sudo does not reset the the $HOME environment variable. So, in some cases, you may end up with files owned by root in your user's home directory. For examples and details read the link posted by audiomick.

If you prefer sudo over gksu, then use **sudo -i command**.

---

### Post by wojox on 2010-07-12
> **sisco311 said:**
> By default, sudo does not reset the the $HOME environment variable. So, in some cases, you may end up with files owned by root in your user's home directory. For examples and details read the link posted by audiomick.

If you prefer sudo over gksu, then use **sudo -i command**.

Agreed and since you posted in Kubuntu use [kdesudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Georgia boy on 2010-07-12
So, if you want to do something like the apt-get upgrades and apt-get install you need to do a "sudo" not the "gksudo" right? 

Tom

---

### Post by CharlesA on 2010-07-12
> **Georgia boy said:**
> So, if you want to do something like the apt-get upgrades and apt-get install you need to do a "sudo" not the "gksudo" right? 

Tom

That is correct.

---

### Post by RiceMonster on 2010-07-12
I noticed the title says kubuntu. For graphical applications in KDE, the equivilant is kdesudo, rather than gksudo.

---

