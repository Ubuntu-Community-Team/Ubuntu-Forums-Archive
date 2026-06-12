---
title: "Itunes 8.02 won't install with Wine 1.0.1"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by gerbs on 2009-01-26
I need itunes to purchase certain hard to find songs, but am hitting a snag installing it. 

install to c:\program files\itunes\
installation starts
screen goes black.
when it comes back, there is an error "the installer encountered errors before itunes could be configured."

any ideas on if i need to change wine configuration or something else?

---

### Post by Shpongle on 2009-01-26
you should try the wine hq [http://www.winehq.org]("http://www.winehq.org") for compatability and install issues, or try using an earlier version of itunes

---

### Post by LostMagix on 2009-01-26
I would try a older Itunes, I here people have for 7.3 working ok, i dont know about anything newer

---

### Post by blueridgedog on 2009-01-26
Sometimes I get results with wine by doing the install from a terminal.  Going to the directory where you have the install exe file you can:

wine itunessetup.exe 

Change itunessetup.exe to whatever you downloaded.  Occasionally it carps about a missing file or setting that you can then debug.

---

### Post by gerbs on 2009-01-27
itunes 7.3 installed fine for me. 
thanks for the help.

---

