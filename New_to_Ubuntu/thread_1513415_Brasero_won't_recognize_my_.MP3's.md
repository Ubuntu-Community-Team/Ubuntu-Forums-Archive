---
title: "Brasero won't recognize my .MP3's"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by whistlenut on 2010-06-19
Hello all.  I am using the 32 bit version of Ubuntu 10.04 Lucid Links.  I have installed the Ubuntu-restricted-extras package but Brasero still won't burn my .MP3's.  It says after doing a search for plug ins that it needs an MSword decoder.  This doesn't make sense to me; what do I do next?  Thank you.

---

### Post by MooPi on 2010-06-19
You can install lame from the repository/Synaptic. That should handle your mp3 encoding problem.

---

### Post by mapes12 on 2010-06-19
Also, try using the K3B burning application (it's in Synaptic). IMHO it handles burning more efficiently than Brasero.

EDIT It may not apply to mp3's but make sure you have the codecs from [http://www.medibuntu.org/](http://www.medibuntu.org/) installed.

---

### Post by dixonstalbert on 2010-06-19
if you are still having trouble, check out medibuntu.org . this website has a repository for multimedia codecs that do not come with ubuntu because of licencing issues. (sounds like you need w32codecs package).

this thread [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) tells you how to set up ubuntu to handle most common multimedia tasks

---

### Post by whistlenut on 2010-06-25
Thank you all very much for your help.  I installed both the w32 codecs, and Lame.  Unfortunately, I am still having the same problem.  The message has changed a little.  Now it tells me the required plug in is text/uri-list decoder.  What next?

---

### Post by whistlenut on 2010-06-25
I am also unable to use the alternative burning program suggested as it is incompatible with Orca, the screen reader supplied with Ubuntu.

---

