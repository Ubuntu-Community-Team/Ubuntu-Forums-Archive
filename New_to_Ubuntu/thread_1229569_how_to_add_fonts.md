---
title: "how to add fonts?"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-08-02
Jaunty 64 bit.  Want to add ecofont.

I have downloaded it and placed it in a folder, /home/user/.fonts but still it does not appear as a choice in OpenOffice writer.

The oo help system says to use something called ./spadmin but I couldn't find the directory in which OpenOffice applications reside.

Any suggestions?

---

### Post by longtom on 2009-08-02
Is it a True Type Font?

---

### Post by SunnyRabbiera on 2009-08-02
> **longtom said:**
> Is it a True Type Font?

True type fonts work in openoffice, but do you use Openoffices quick launcher?

---

### Post by raymondvillain on 2009-08-02
Yes it is a true type font:

[HTML]http://www.ecofont.eu/ecofont_en.html[/HTML]

Spranq_eco_sans_regular.ttf

that is a q in Spranq, not a g.

Can anyone say in which directory reside the oo files?

---

### Post by SuperSonic4 on 2009-08-02
Have you updated the cache via ```
fc-cache
```

---

### Post by SunnyRabbiera on 2009-08-02
> **raymondvillain said:**
> Yes it is a true type font:

[HTML]http://www.ecofont.eu/ecofont_en.html[/HTML]

Spranq_eco_sans_regular.ttf

that is a q in Spranq, not a g.

Can anyone say in which directory reside the oo files?

the hidden fonts folder applies to all apps.
Do you use the open office quick launch or have it running in background?
Also try logout

---

### Post by raymondvillain on 2009-08-02
Thanks for all the help, folks.  I did try everyone's suggestions.

I finally figured out what to do.  The directory I used is /usr/share/fonts/truetype/freefont and I just put it there even though it is not a freefont.

Anyway, now it is available on open office apps.

I'm going to mark this solved.

---

