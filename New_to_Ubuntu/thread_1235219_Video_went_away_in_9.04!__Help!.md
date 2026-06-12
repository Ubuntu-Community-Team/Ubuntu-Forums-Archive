---
title: "Video went away in 9.04!  Help!"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by john wagner on 2009-08-08
Hi!
Not really sure what happened...  My Dapper crashed a month ago, so I reformated and installed Ubuntu 9.04 on a clean system.

OUT of the box, everything worked fantastic!  All drivers, all videos, everything ran great on my HP Pavillion 160gig HDD 2 gig RAM laptop.
Two days ago, system locked up.  Couldn't do anything at all.  So, I reloaded 9.04 from scratch.

Works fine.  Just no video now.  FLV doesn't seem to work at all (even getting the plugins for mozilla/firefox, I'm running in Firefox).

Tried everything.  What gives???  Even lost the video I was able to view in my Dapper!?!

john

---

### Post by Redache on 2009-08-08
Did you try installing the ubuntu-restricted-extras package?.

This package contains most of the common codecs needed to play videos.

---

### Post by 3rdalbum on 2009-08-08
Things have changed a lot since Dapper :-)  The "ubuntu-restricted-extras" package contains most of what you need for (what most would consider) a modern and productive home system, so make sure you install that. I don't think it pulls in the gstreamer codecs - so make sure you install the gstreamer "bad" and "ugly" packages.

Finally, add the Medibuntu repository and install libdvdcss2 and non-free-codecs; the former adds DVD decryption support, and the latter adds the "w32codecs".

---

### Post by john wagner on 2009-08-08
I did all that!  Then I went crazy and tried all the oddball stuff.  Nada, zip.  
What kills me, is that it worked fine, out of the box on the first install.  I was running 9.04 with zero problems for over a month!  Closer to two...
Then, this.  And I reloaded with the same iso I used initially.  Downloaded all the updates, opened the repositories, etc, etc...  Nada.
Reformated several times with different iso's (all sum checked), did an HDD check, all fine.  No video.

VERY irrritating.  

john

---

### Post by john wagner on 2009-08-09
just a bump....  any more advice?

---

### Post by john wagner on 2009-08-16
> **john wagner said:**
> just a bump....  any more advice?

another bump.
No one???  I'm screwed?
What about a reformat with an install of an earlier (ie: non updated) 9.04?

---

