---
title: "Changing FIlesystem Files"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by MikeYoung on 2009-09-23
Hi, I have ultimate edition ubuntu (jaunty) 9.04 I am trying to do some tricks I am reading. However they require you to change or add to folders in the filesystem drive and it will not let me says that I am not the owner.

---

### Post by rampageoberon on 2009-09-23
You need to be root user (or have sudo privileges) to create directories outside your home directory by default. If you're not the owner you may not be able to do what you need. Sorry

---

### Post by LewRockwell on 2009-09-23
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

[http://en.wikipedia.org/wiki/Mkdir](http://en.wikipedia.org/wiki/Mkdir)

[http://en.wikipedia.org/wiki/Touch_(Unix](http://en.wikipedia.org/wiki/Touch_(Unix))

.

---

### Post by MikeYoung on 2009-09-23
I am the owner I am very new to linux. How would I make myself administrator on my computer I am not good with the command line at all. thanks for the help

---

### Post by philinux on 2009-09-23
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Be careful changing system files. You could end up with a broken system very easily. Double check what you're doing and make notes so you can go back.

---

### Post by arpanaut on 2009-09-23
You are the administrator of your 'puter but linux/Ubuntu do things differently.

See:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This will help too:  [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

Good Luck!

---

### Post by LewRockwell on 2009-09-23
> **MikeYoung said:**
> I am the owner I am very new to linux. How would I make myself administrator on my computer I am not good woth the command line at all. thanks for the help

honestly, most of us have learned how to fix things...by breaking them first...

a clone of your fresh install after fully updating will allow you to quickly reset your system via the safe, secure, and functioning clone

we use Clonezilla regardless of the operating system we are cloning

.

---

### Post by MikeYoung on 2009-09-23
ok thanks I guess I cant expect to learn linux overnight took awile for me to learn windows.

---

### Post by Marflus on 2009-09-23
Exactly. If you read the links posted by others you should be able to figure out what needs doing. Ubuntu will happily let you edit any (or all) files on your hard drive if you want it to, you just have to ask nicely :)

[http://xkcd.com/149/](http://xkcd.com/149/)

(Ok, so everyone uses that link, but it's actually appropriate this time >.>)

---

