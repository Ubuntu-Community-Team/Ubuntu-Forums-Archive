---
title: "I just want 80 * 25 without the funky character set"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by davecgs on 2009-03-25
Hey guys.  In the console (NOT the terminal window), I just want plain old 80 * 25   Ubuntu seems to change the characters to a funky CGA like character set.  I'm from the old DOS world and when I hope to a tty screen, I want it to look like an old tty screen (e.g. if you booted up in DOS)

Is there a kernel switch for that.  In Fedora I used NOMODESET and it worked great.  What is the equivalent in Ubuntu. 

Thanks...

---

### Post by davecgs on 2009-03-26
Found the answer.  

Nano /etc/default/console-setup

1)changed CODESET=”Uni1” to “CODESET=Lat15”
2)changed FONTFACE=”Fixed” to FONTFACE=”VGA”


dpkg-reconfigure console-setup

will also let you do it.

---

