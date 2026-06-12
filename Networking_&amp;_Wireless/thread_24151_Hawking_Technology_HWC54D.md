---
title: "Hawking Technology HWC54D"
date: 2005-04-05
forum: Networking &amp; Wireless
---

### Post by smiting2000 on 2005-04-05
has anyone successfully gotten a Hawking Technology HWC54D wireless network card to work?  they don't officially support linux with this exact card but some of them do.  does anyone know of a way to get this to work? i am new to any kind of Linux distribution so i don't really know how to do much so if there is a fairly easy way, i would like to know.

thank you,
ryan

---

### Post by dataw0lf on 2005-04-06
ndiswrapper supports the HWC54D.  I'm unsure what chipset it uses (it might be Prism, if it is, then you won't have to use ndiswrapper).

---

### Post by smiting2000 on 2005-04-07
ok, thank you, i will see if that works for me.

---

### Post by smiting2000 on 2005-04-08
when i try to install this, i do everything it says to do but it gives me this:

ryan@RyanBuss:/usr/src$ sudo tar jxvf ndiswrapper-source.tar.bz2
tar: ndiswrapper-source.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ryan@RyanBuss:/usr/src$


i am new to this, so i have no clue what it means.  can someone tell me what i need to do to fix this?

thank you

---

