---
title: "Update - 99% - waiting for headers"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Falc7 on 2010-02-23
Recently it has started taking ages to look for new updates, it does the first 99% very quickly, but get stuck at 99% - waiting for headers, for about 3 minutes. It never used to take so long, is there something i can do?

At the end it tells me this:
Get: 3 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Get: 4 [http://dl.google.com](http://dl.google.com) stable/main Packages [871B]
Fetched 3,601B in 2min 0s (30B/s)
Reading package lists... Done
jamie@jamie-kubuntu:~$

---

### Post by Fougner on 2010-02-23
Just remove the google chrome repository from software sources. That's what I did. Alas, you have to  upgrade chrome manually.

---

### Post by IceBadger on 2010-02-23
I came here for the same issue and have google-chrome installed.

I would not disable the chrome repo yet.  As I was logging into this forum, my apt-get update finished, saying it took about 2 min to complete.  I know that the update usually takes quicker, but the chrome repo is just slow i think.

Just be patient.](*,)

---

### Post by Falc7 on 2010-02-24
ah ok, thats fine as long as the problem isen't on my end

---

### Post by CaptainMark on 2010-02-24
its happening with other repos, i dont have google chrome repo added but i just had the same issue.

---

### Post by kopa on 2010-03-01
I have these issues with the dl.google.com repo too. My geographic location: Europe/Austria

---

### Post by ikt on 2010-03-01
> **kopa said:**
> I have these issues with the dl.google.com repo too. My geographic location: Europe/Austria

Austria :)

[http://www.youtube.com/watch#playnext=1&playnext_from=TL&videos=BWWvr_tN0Pc&v=mqVzRD_nWLQ](http://www.youtube.com/watch#playnext=1&playnext_from=TL&videos=BWWvr_tN0Pc&v=mqVzRD_nWLQ)

Throw another shrimp on the barby!

..


The repo seems to be working fine for me: Oceania/Australia

---

### Post by kopa on 2010-03-01
nice, didn't know that one. :)

> **ikt said:**
> Austria :)

[http://www.youtube.com/watch#playnext=1&playnext_from=TL&videos=BWWvr_tN0Pc&v=mqVzRD_nWLQ](http://www.youtube.com/watch#playnext=1&playnext_from=TL&videos=BWWvr_tN0Pc&v=mqVzRD_nWLQ)

Throw another shrimp on the barby!

..


The repo seems to be working fine for me: Oceania/Australia

---

### Post by DirtyBeets on 2010-03-01
I'm having the same issue with google.

One thing I'm curious about is what is the difference between Hit and Ign?

---

### Post by ikt on 2010-03-03
> **DirtyBeets said:**
> I'm having the same issue with google.

One thing I'm curious about is what is the difference between Hit and Ign?

I'm assuming hit means 'check out what's on the server' and ign means ignore if what's on the server is the same as what's on your computer.

Happy to be corrected.

---

### Post by Penguin Guy on 2010-03-18
I'm having the same issue, and I also have Chrome installed.

---

