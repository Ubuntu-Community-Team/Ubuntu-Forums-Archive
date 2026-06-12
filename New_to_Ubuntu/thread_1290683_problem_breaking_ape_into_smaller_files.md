---
title: "problem breaking ape into smaller files"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by vividia on 2009-10-13
I downloaded a large ape with a cuesheet.  I have used shnsplit to break other files but I've never done ape.  I tried and got this response

> cuebreakpoints inconnu.cue | shnsplit -o flac inconnu.ape
shnsplit: warning: failed to read data from input file using format: [ape]
shnsplit:          + you may not have permission to read file: [inconnu.ape]
shnsplit:          + arguments may be incorrect for decoder: [mac]
shnsplit:          + verify that the decoder is installed and in your PATH
shnsplit:          + this file may be unsupported, truncated or corrupt
shnsplit: error: cannot continue due to error(s) shown above


I shortened the name of the files and took out the spaces just to make things easier.  Also, I have no idea what codecs and/or libs I need to make this work if that is the case.

Any ideas?

Viv

---

### Post by vividia on 2009-10-16
I figured it out anyways and I feel a bit like an idiot.  I'm blaming my recent tonsillitis for that. :P  I thought I had what I needed but I went and rechecked everything and lo and behold, I didn't have mac support.  

If anyone comes here with the same problem, [here]("http://freestorage.ro/tucbdv6q7s1u")'s where to mac package for ape.  

Viv

---

### Post by rolandrock on 2010-06-25
Thanks Viv.  I was thrashing around cursing monkeys when I found your post.  I for one have no problem taking instruction from a lady.

Warm Regards

---

### Post by jamesisin on 2010-08-29
For those interested I have a set of instructions for this:

[http://www.soundunreason.com/InkWell/?p=1282](http://www.soundunreason.com/InkWell/?p=1282)

(You will also find links for doing the same with track APE files and album length FLAC files.)

---

