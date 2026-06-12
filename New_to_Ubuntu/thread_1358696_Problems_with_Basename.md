---
title: "Problems with Basename"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by nmaster on 2009-12-18
I realized while trying to write a script that basename isn't very good.  These are just a few examples:
```

$ basename LockhartsLament.djvu 
LockhartsLament.djvu
neal@neal-laptop:/home/neal/Documents 
$ basename lucia.jpg 
lucia.jpg
neal@neal-laptop:/home/neal/Documents 
$ basename Spring_2009.ics
Spring_2009.ics

```
I'm a bit surprised, since .jpg and .djvu are common extensions.

What is a good alternative?  I need the basename, but obviously basename doesn't always work.

---

### Post by The Cog on 2009-12-18
Read the manual.
"Print NAME with any leading directory components removed.  If specified, also remove a trailing SUFFIX."
The command to view the manual is **man basename**. Use **q** to quit. You must tell it the suffix to remove.

---

### Post by Mornedhel on 2009-12-18
As The Cog says, the manual is clear on what basename does. Here are a few examples :

```
$ ls -F
blah.xml somefolder/
$ basename somefolder/blah.pl
blah.pl
$ basename blah.xml
blah.xml
$ basename blah.xml .xml
blah
```

Alternatively, if you're using bash (I'm not sure this will work in sh or zsh), you could use the following construction :

```
FILE=blah.xml;
echo ${FILE%.*}
```

(should return .xml)

Or even to return the extension only :

```
FILE=blah.xml;
echo ${FILE#${FILE%.*}}
```

(should return blah)

---

### Post by nmaster on 2009-12-20
thanks boss.  i feel like a dufus for misunderstanding the man page.  i still learn better from seeing examples than from reading manuals.

---

### Post by The Cog on 2009-12-21
Sorry I was a bit terse - I was felling a bit tired at the time.

The suffix that basename removes doesn't have to start with a dot - it will remove any chunk of text you specify from the end of the file. Which is why you have to specify - the assumption that the (last?) dot and anything following is a suffix is an assumption induced by familiarity with other operating systems such as DOS, OS/2, windows. Apart from a leading dot being a hint towards file hiding, a dot in a filename has no significance in unix/linux.

---

