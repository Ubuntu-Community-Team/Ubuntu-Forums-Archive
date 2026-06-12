---
title: "How To Use cp In A Script"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2009-06-12
Okay, here's what I'm trying to do:  I dug out my old X-Wing Win95 game and played it.  It updated my pilot, who is named onyx.plt.  Back in the day, I had a .bat file that would copy my updated onyx.plt to several other *.plt files so that I could use that pilot as a super-wingman.  Since I'm now running X-Wing under 9.04, I wanted to make a script (that's what the functional equivalent of a DOS .BAT file is, right?).  I looked stuff up out there on the interwebs, and I changed my old file from this (MS-DOS):
```
copy onyx.plt 1.plt
copy onyx.plt 2.plt
copy onyx.plt 3.plt
copy onyx.plt 4.plt
copy onyx.plt 5.plt
copy onyx.plt mulder.plt
copy onyx.plt scully.plt
copy onyx.plt no-use.plt
``` to this:
```
cp -u onyx.plt 1.plt
cp -u onyx.plt 2.plt
cp -u onyx.plt 3.plt
cp -u onyx.plt 4.plt
cp -u onyx.plt 5.plt
cp -u onyx.plt mulder.plt
cp -u onyx.plt scully.plt
cp -u onyx.plt no-use.plt
``` by which I'm trying to say "copy (update only) onyx to whatever"

However, when I run the script by double-clicking on it and then clicking "Run in Terminal", I get *extra* files with the names above, but they don't replace the old ones.  The new names seem to have an extra space after .plt.

Now, this is my first-ever script in Linux, and I am very, very ignorant.  Would someone please help me out of my ignorance and tell me what I'm doing wrong?  I'm happy to read something else, but I'm afraid I'll end up looking in the wrong spot.

Thanks in advance.

Eric

---

### Post by CJ Master on 2009-06-13
I'm not sure what the -u option is for, I never use that option. Try it without.

---

### Post by Eric Qel-Droma on 2009-06-13
The site that I found that had the syntax and options said that "-u" only overwrites if the file being copied is newer than the file being overwritten.  I thought maybe it would help to force an overwrite.

Just tried it without "-u" same thing:  files get copied, but they have a space or something right after the end of the name so that the system sees them as separate files.

---

### Post by Eric Qel-Droma on 2009-06-13
Okay, this is weird.  There must be some sort of copy/paste artifact in there somewhere.  I just went through the script and deleted twice after the end of each line, then hit enter twice to clearly separate the lines out.  Now it's backing up the names perfectly.  Weird.  

I'm not going to mark this "solved" until I know why it's not working, but at the same time, there it is.

---

### Post by PGScooter on 2009-06-13
Hi Eric,

Glad you figured out a temporary work-around. That does seem like a strange problem. For this type of task, I would highly recommend the rsync command over cp. You should have rsync already installed. It has a lot of options though, and might take awhile for you to figure them out, so if you don't want to spend the time, I guess stick with cp while it's working.

And by the way, I don't think you can mark ghreads as solved anymore. I believe that feature was removed.

---

### Post by asmoore82 on 2009-06-13
[http://en.wikipedia.org/wiki/CRLF#History](http://en.wikipedia.org/wiki/CRLF#History)

^Basically, Windoze _*still*_ uses the newline sequence
from prehistoric teletype machines; Unix systems do not.

---

### Post by nandemonai on 2009-06-13
> **asmoore82 said:**
> [http://en.wikipedia.org/wiki/CRLF#History](http://en.wikipedia.org/wiki/CRLF#History)

^Basically, Windoze _*still*_ uses the newline sequence
from prehistoric teletype machines; Unix systems do not.

Beat me to it. This is often a problem when copying text from Windows text files.

---

