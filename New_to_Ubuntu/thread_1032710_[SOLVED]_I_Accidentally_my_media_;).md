---
title: "[SOLVED] I Accidentally my /media ;)"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by dubhear on 2009-01-06
[QUOTE=dubhear;6506065][[IMG]http://img525.imageshack.us/img525/285/screenshotcg9.th.png[/IMG]](http://img525.imageshack.us/my.php?image=screenshotcg9.png)
[[IMG]http://img511.imageshack.us/img511/1444/screenshot1ir4.th.png[/IMG]](http://img511.imageshack.us/my.php?image=screenshot1ir4.png)

so here's my quote from thread:

[http://ubuntuforums.org/showthread.php?t=1025863](http://ubuntuforums.org/showthread.php?t=1025863)

so here you see i fuxxxored my /media?!?

---

### Post by LowSky on 2009-01-06
so why did you create a new thread?

also your links dont work

---

### Post by dubhear on 2009-01-06
> **LowSky said:**
> so why did you create a new thread?

also your links dont work


so why not?
since this has nothing to do with my dvd-problem

more like my /media problem. and if someone had posted this kind of problem before, you show it to me, with a solution.

in that case, sorry about new thread.

and why am i not getting any help from this community if anyone can check my links or advice me to upload images correctly!!!

i expected more...

---

### Post by oldos2er on 2009-01-06
"why am i not getting any help from this community"

 Give it time. Everyone here is a volunteer; and not everyone has the answer to every question or problem that arises.

---

### Post by dubhear on 2009-01-06
> **oldos2er said:**
> "why am i not getting any help from this community"

 Give it time. Everyone here is a volunteer; and not everyone has the answer to every question or problem that arises.

Heey! i respect every reply from bottom of my heart.

And you say i should expect that you don't help me?!? well, i'll just sit here with my /media folder still ****** up. reading what i just said, how nice

and with "why am i not getting any help from this community" is so far from context, i didn't mean to insult OUR community. i just expected more...

maybe these settings don't come easy, maybe it is easier now to start a fight about this?!? maybe i can't stay patient any more?!? or maybe this is just one reply that you really should understand and pass by without anything to defend. or get angry with....

...and get over with this problem, just like we always did.

---

### Post by cariboo on 2009-01-06
If you want to attach images to a post, you have to be in the advanced editor, then scroll down until you see manage attachments, you can add images there.

As for your /media problem, can you explain what it is you need help with, you title is not very descriptive

> Re: I Accidentally my /media ;)

If you deleted it, why not just  recreate it. in a terminal type the following:

```
cd /
```

this changes driectories to /, next

```
sudo mkdir -p media/cdrom0
```

this creates the media and cdrom0 directoriews next

```
cd media
```

you should now be in the media directory, the next thing to do is to symlink cdrom0 to cdrom:

```
sudo ln -s cdrom0 cdrom
```

Now if you haven't changed anything else it should work the way it was supposed to.

Jim

---

