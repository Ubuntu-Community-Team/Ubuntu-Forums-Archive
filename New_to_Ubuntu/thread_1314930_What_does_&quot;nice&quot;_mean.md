---
title: "What does &quot;nice&quot; mean?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Nenu on 2009-11-04
Hi,

I have seen "NICE" in connection with things that are running but I have no idea what it actually means, and what would it mean if it stopped being nice (and how can I make sure that doesn't happen).

I am sure this is a stupid question and one that has been answered before...but I am an absolute beginer so this seemed the logical place to ask :confused:

Nenu ):P

---

### Post by unamanic on 2009-11-04
nice has to do with how likely the system is to bump it out of the way to perform other tasks.  A nice of 10 means the process is more likely to wait, while a -10 will have it pushed to the front.  0 is generally the default and you need super user privledges to go negative.

---

### Post by yeats on 2009-11-04
Basically, nice is a program that assigns a lower priority for resources to specific programs and is a remnant of the days when many users shared a single UNIX system and could use nice to let other people's programs run before their own.  You can open a terminal (Applications -> Accessories -> Terminal) and type:

```
man nice
```

for more details.

---

### Post by Ericyzfr1 on 2009-11-04
It indicates the status of a process priority if I am correct.

---

### Post by stinger30au on 2009-11-04
if a female tells you that your nice, it means she aint interest in you, move on ):P

---

### Post by anewguy on 2009-11-04
Dang, and I thought I had them all fooled!!

Dave :)

---

### Post by movieman on 2009-11-04
> **chrissharp123 said:**
> Basically, nice is a program that assigns a lower priority for resources to specific programs and is a remnant of the days when many users shared a single UNIX system and could use nice to let other people's programs run before their own.

It's not just for multi-user systems: it's handy if you want to run something in the background (e.g. video compression, etc) while you keep working, because you can 'nice' the background task so it mostly uses idle cycles.

---

### Post by jnew93 on 2009-11-04
> **stinger30au said:**
> if a female tells you that your nice, it means she aint interest in you, move on ):P

True dat. Also, nice is basically the priority level of processes. Although I was not aware of it's origins and early purpose. You learn something every day! :D

---

### Post by Nenu on 2009-11-11
Thank you all, I can now ignore it and stop worrying (I don't feel confident enough yet to even attempt to change the priority of anything yet).

And as a girl (well a woman lol) I would like to say you are all really nice ;)

Nenu

---

