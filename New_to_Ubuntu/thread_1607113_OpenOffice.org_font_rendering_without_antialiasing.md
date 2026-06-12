---
title: "OpenOffice.org font rendering without antialiasing"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-10-27
Hi guys, but of a longshot, but I figured I'd try here. OpenOffice exhibits weird behaviour with some fonts (I believe otf may be the common factor here). As you can see in the sample shot, the text is without antialiasing, but if I zoom *out* just 5%, the problem goes away.

You can also see italic text does not have the same issue.

[IMG]http://i.imgur.com/aMaLZ.png[/IMG]

I upgraded to the 3.3 RC to see if that made any difference; it did not.

---

### Post by Pas_sa on 2010-10-30
I've been doing some investigations - these problems are replicated in Word 2007 running in Wine and somewhat in Abiword:

[IMG]http://i.imgur.com/RLNSS.png[/IMG]

The aliased fonts are all OTF at sub <15 size. Only OTF fails to anti-alias at that size. TTF fonts are always antialiased (down to size 1). Abiword is similar but can anti-alias OTF beyond size 12.

So my conclusion is.. OTF font rendering issue in Ubuntu? I've poked around on the net but haven't found a mention of this issue anywhere. Does anyone have a similar problem? Any possible solutions?

---

### Post by stmiller on 2010-10-30
My fonts all seem to be antialiased, if that helps. :/ I'm not sure where to check to change this in Ubuntu. :confused:

[IMG]http://imgur.com/ce0Tt.png[/IMG]

---

### Post by Pas_sa on 2010-10-30
Hmm interesting. Garamond is antialiased for me too - but Calibri and Cambria still aren't. It happens in any application it seems:

[IMG]http://i.imgur.com/CXv0M.png[/IMG]

---

### Post by jtarin on 2010-10-30
This is Wine related, not Ubuntu.I use Cross-over for Wine and it still exhibits itself in MS Word.

[A fix you might want.]("http://www.webupd8.org/2009/09/enable-smooth-fonts-in-wine-linux.html")

---

### Post by Pas_sa on 2010-10-30
Thanks for the reply - but if you looked over the thread, you'll see the exact same problem occurs with OpenOffice.org and Abiword. I'm fairly sure neither of those are running under Wine.. :P

---

### Post by jtarin on 2010-10-31
Shame on me!

---

### Post by Heavenly Evil on 2010-11-11
What fixed it for me was following the suggestion in this thread: [http://ubuntuforums.org/showthread.php?p=10105323](http://ubuntuforums.org/showthread.php?p=10105323)

---

