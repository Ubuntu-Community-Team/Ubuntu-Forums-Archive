---
title: "Flash issues on x64"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by nishant.singh28 on 2010-02-02
I have the latest prerelease version of Flash 10 on my Karmic x64 machine. But it's using too much CPU. It struggles to play 480p Youtube vids in fullscreen while SMPlayer happily plays 720p H264 encoded movies while Media coder is running. Even in normal conditions without Mediacoder at work, playing 720p Youtube vids takes CPU usage to ~40%while in smplayer it barely touches 20%. And sometimes, audio simply disappears and I've to restart firefox. What is going on?

---

### Post by lovinglinux on 2010-02-02
Welcome to the Adobe nightmare. I guess the problem is that flash doesn't use gpu acceleration as mplayer does. There are some [tips in my tutorial](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1), but nothing miracle. Notice that the introduction of that section describes exactly what you have observed.

---

### Post by Shark_AtK12 on 2010-02-02
[FONT=Century Gothic][SIZE=2]I had the same problem with youtube videos. Playing them full screen caused them to stutter and use the CPU badly. I browsed the net and found out the same thing that lovingLinux said. I am unable to view his link as i am at work but enabling GPU acceleration for Flash seemed to help. Cant rememember for the life of me what the command was...[/SIZE][/FONT]

---

### Post by skymera on 2010-02-02
Do you have the Flash10 native 64bit installed?

This helped me a lot.
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

Copy the file to:

```
 /home/USER/.mozilla/plugins/ 
```

---

### Post by nishant.singh28 on 2010-02-02
I've done both the things and the only change is the CPU usage has gone down a teeny little bit by say 2% but it  still is too high. I mean 40% usage for a flash video!!!

---

### Post by samantha_ on 2010-02-02
I guess windows is the only OS where flash works completely right....
even on mac osx, the cpu spikes up to about 30% on both cores just to play some lysol flash ads.....

---

### Post by nishant.singh28 on 2010-02-02
Is there any alternative to flash in the repos?

---

### Post by audiomick on 2010-02-02
From what I have seen here, the advice from lovinlinux is about the best you can get.

---

### Post by ikt on 2010-02-02
[http://ikt.id.au/?p=5](http://ikt.id.au/?p=5) ;)

> It struggles to play 480p Youtube vids in fullscreen

If you really want to watch the high def videos in full screen you can try downloading the high definition videos directly off youtube and then playing them in vlc/totem etc:

[http://ikt.id.au/?p=45](http://ikt.id.au/?p=45)

Overall though the good news is that flash is on its way out!

[http://daringfireball.net/2010/01/blue_boxes](http://daringfireball.net/2010/01/blue_boxes)

---

### Post by samantha_ on 2010-02-02
> **nishant.singh28 said:**
> Is there any alternative to flash in the repos?

swfdec and gnash. Although they are highly incomplete versions of flash, swfdec seems capable of playing youtube for a lot of people.

---

### Post by audiomick on 2010-02-02
> **samantha_ said:**
> ... seems capable of playing [COLOR="Red"]yourube[/COLOR] for a lot of people.

if that wasn't a typo, it's very good. If it was a typo, it's still good...;)

---

### Post by samantha_ on 2010-02-02
> **audiomick said:**
> if that wasn't a typo, it's very good. If it was a typo, it's still good...;)

fixed ;)

---

### Post by Thelasko on 2010-02-02
> **lovinglinux said:**
> There are some [tips in my tutorial](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1), but nothing miracle. Notice that the introduction of that section describes exactly what you have observed.

Hmm, haven't found that tidbit before.  Thanks!

---

