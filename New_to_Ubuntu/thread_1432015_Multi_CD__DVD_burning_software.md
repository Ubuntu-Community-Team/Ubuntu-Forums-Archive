---
title: "Multi CD / DVD burning software"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by Charlie Chick on 2010-03-17
Hello Everybody,

I have an Ubuntu computer with 6 CD / DVD drives. Is there any open source software that will allow me to burn 6 copies at once?

Thanks,

Charlie

---

### Post by aeiah on 2010-03-17
they should all let you do it since you just specify the target drive.. if you're planning on burning like 200 audio cds or something then you might want to automate it with a script.

depending on how things are set up, you may find that it isnt much quicker using all 6 at once because you may hit a bottleneck elsewhere

---

### Post by Charlie Chick on 2010-03-17
So Brasero and K3B will allow me to make 6 copies at a time?

---

### Post by mikechant on 2010-03-17
> So Brasero and K3B will allow me to make 6 copies at a time? 

Ubuntu/Linux will allow such things to be done with no OS software issues, but some programs are deliberately written so that you can't run multiple copies at once (e.g. they have a 'lock file' or something so if you start a second instance it will just end immediately).

I would experiment with just two instances first. If you can't get them both to run at once under one userid you could set up a second userid and run one instance under each user.

(The following is irrelvant if you already know this will work from a hardware point of view (e.g. you've already burnt six discs at once under windows or something):)

Assuming you can get multiple burns running at the same time, either under one or multiple users, you may well find you will get hardware conflicts causing extreme slowdowns and therefore bad burns. This will depend a lot on how the six drives are connected (bus capacities etc.), if your PC is really capable of feeding as many as six at once, and whether the source for the burn is fast enough (e.g. trying to burn six different DVD size isos from the same hard drive would probably be a problem; trying to burn multiple copies of a single CD sized iso would probably be better because the whole file might well get cahced in RAM).

Anyhow, it sounds like an interesting experiment!

---

### Post by Charlie Chick on 2010-03-17
Thanks for the info. Apparantly, Nero allows you to burn multiple discs at once but obviously I want open source software!

---

