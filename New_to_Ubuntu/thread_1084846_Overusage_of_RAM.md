---
title: "Overusage of RAM"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Grifulkin on 2009-03-02
I installed Kubuntu 8.04 because I personally like KDE 3.0 over KDE 4.1 or 4.2.  So anyways I looked at my system monitor and found that 2.5 gb of my ram were being used, I have 4 but I was taken back as to how much was being used can anyone tell me why, or have anything inclination as to why so much is being used?  Thank you.

---

### Post by SuperSonic4 on 2009-03-02
I believe KDE 4.2 actually uses less ram than 3.5.10, not sure why

top says I'm using just under 3gb on mine and htop says 1219mb

---

### Post by The Cog on 2009-03-02
Linux tends to use unused RAM as disk cache rather than leave it fully unused. Are you sure that's not what you are seeing?

---

### Post by mister_pink on 2009-03-02
Run "free -m" in a terminal and post the output here in [code] blocks

---

### Post by Grifulkin on 2009-03-03
> **mister_pink said:**
> Run "free -m" in a terminal and post the output here in ```
 blocks

[code]             total       used       free     shared    buffers     cached
Mem:          3963       3550        412          0       1282       1892
-/+ buffers/cache:        375       3588
Swap:          953          0        953

```

---

### Post by bodhi.zazen on 2009-03-03
Linux uses RAM very differently from Windows and the rule of thumb is "unused RAM is wasted RAM"

From your post you are using much less RAM (See the +/- buffers/cache line).

See also : err ... I had a nice link can not find it now, sorry, try google :)

EDIT: Ah, found it :twisted:

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)
    [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

### Post by handy on 2009-03-03
***@bodhi.zazen:*** Thanks. :) 

That 2nd link is a beauty, I'll use that in future when the RAM question arises.

---

### Post by Grifulkin on 2009-03-03
Thank you everybody :)

---

