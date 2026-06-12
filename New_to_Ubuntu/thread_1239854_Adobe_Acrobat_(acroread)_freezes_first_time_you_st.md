---
title: "Adobe Acrobat (acroread) freezes first time you start it"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by dugh on 2009-08-14
The first time I open a pdf file (on the desktop or in firefox), everything freezes for about 20 seconds or so.

This has been going on for a year now.  Is there any fix or workaround?  I know I can use Evince, which is fine for most pdfs, but evince didn't print some pdfs correctly so I've been using acroread instead.

I thought I remembered reading at one point that it might be something like a dns lookup or something?

---

### Post by LowSky on 2009-08-14
ope it using a terminal window, report the errors.

How did you install it, that might be the underlying problem... and how old is your hardware?

---

### Post by LewRockwell on 2009-08-14
[http://www.foxitsoftware.com/downloads/index.php#editor](http://www.foxitsoftware.com/downloads/index.php#editor)

.

---

### Post by dugh on 2009-08-17
I found the solution.  Medibuntu no longer provides acroread - they silently removed it.  This wasn't documented anywhere.  Even the Ubuntu Guide site still refers to using medibuntu to install acroread.

You have to completely remove acroread (I also deleted the <home>/.adobe/Acrobat folder), and then enable the Canonical Partner repository in Software Sources.

Now it only freezes for a few seconds instead of 15-20.  I went to Edit->Preferences also and unchecked "check for updates" so hopefully it will freeze even less next time I reboot and open up the first pdf.

I updated the Medibuntu page on the Ubuntu wiki to reflect this new information.

---

### Post by dugh on 2009-08-17
Although be forewarned, Adobe Acrobat 9 has a whole new bug - not being able to save a copy of a pdf to certain drives:
[http://ubuntuforums.org/archive/index.php/t-1141801.html](http://ubuntuforums.org/archive/index.php/t-1141801.html)

But that's easily worked around - just use Firefox's save as dialog instead (if reading pdf in browser), or just manually control-drag the file to copy it to the new location.

---

