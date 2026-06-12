---
title: "audio cd extractor cd rom not found?"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by soryu on 2009-12-23
i can play the cd with vlc but i can't copy  to my hard drive.

brasero does nothing. it just tells me no available disc.
and audio cd extractor cant find a cd-rom.

how do i fix this ?
can i copy the cd with VLC?

---

### Post by Geoff918 on 2009-12-23
Have you added the medibuntu repository and installed libdvdcss2 (I think that's the one?)

You may have problems with copy-protected CDs and DVDs without the driver there. It's a legal issue, it doesn't come with Ubuntu by default.

---

### Post by soryu on 2009-12-23
how do i install that? thank's

---

### Post by Geoff918 on 2009-12-23
My fault, I meant to clarify that.  Here's the repository (you can copy paste that into a terminal window):

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

Here's a complete how to guide as well:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

EDIT:

Oh yeah, and finally:

sudo aptitude install libdvdcss2

---

### Post by SuperSonic4 on 2009-12-23
Have you tried abcde? It's a command line ripper but does the job well

---

### Post by soryu on 2009-12-23
i installed the repository and libdvdcss2,but same problem.

---

### Post by soryu on 2009-12-23
just installed abcde,but how do i use it?

---

### Post by SuperSonic4 on 2009-12-23
At it's most basic type ```
abcde
``` in a terminal

More complicated options

```
abcde -o ogg 2
```

You can extract to mp3 if you like, change ogg or flac to mp3

---

### Post by soryu on 2009-12-23
asking for cddbchoices?

---

### Post by SuperSonic4 on 2009-12-23
> **soryu said:**
> asking for cddbchoices?

It's the CD text, usually good because it means you don't have to tag it yourself. (Press q if there is more than one option) then Pick a number or press n

---

### Post by soryu on 2009-12-23
GNU nano 2.0.9 File: ...de.ca0fe30f/cddbread.1           

210 misc ca0fe30f CD database entry follows (until termina$
# xmcd
#
# Track frame offsets:
#        150
#        6479
#        28465
#        50203
#        68153
       [ Read 63 lines (Converted from DOS format) ]
^G Get He^O WriteO^R Read F^Y Prev P^K Cut Te^C Cur Pos
^X Exit  ^J Justif^W Where ^V Next P^U UnCut ^T To Spell

what do i do now? sorry i'm a noob.

---

