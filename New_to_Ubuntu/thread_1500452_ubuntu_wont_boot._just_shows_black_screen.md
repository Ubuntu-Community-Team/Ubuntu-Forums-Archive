---
title: "ubuntu wont boot. just shows black screen"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by insanity99 on 2010-06-03
hey, last night i was really happy because i made a proper install on ubuntu, whereas previously i was on WUBI. everything seemed really fine i did the multimedia guide and installed some essential software. i even restarted a few times to be sure. but the next day it wont boot. it just shows a black screen. i have tried recovery mode, updated grub and chose to boot but it was in CLI mode so i forced shutdown cause i cant do anything there.

what can i do? i also tried the other kernels thats where listed.

thanks.

EDIT: if it helps i am on ATI graphics card.

---

### Post by ThesaurusRex on 2010-06-03
Ensure the live CD isn't still in your CD tray. Check your connections. If you continue to have issues, try booting with a live CD. If the screen is still blank, your graphics card may be dead (or loose). My Windows machine (running Windows ME) broke down a couple years ago with this same issue, and the video card just stopped working.

---

### Post by insanity99 on 2010-06-03
it works through the live CD and windows is working fine so i guess its not my graphics card. what should i do now?

---

### Post by ThesaurusRex on 2010-06-03
Are you using 9.04 or 10.04? Regardless, I would Google the error like mad until I got frustrated because nothing worked then reinstall.

---

### Post by insanity99 on 2010-06-03
im on 9.10

---

### Post by ThesaurusRex on 2010-06-03
This user seemed to have a similar problem. The #6 response looks promising:

[http://ubuntuforums.org/showthread.php?t=1376543]("http://ubuntuforums.org/showthread.php?t=1376543")

> **insanity99 said:**
> im on 9.10

Out of curiosity, any particular reason for not going 10.04?

---

### Post by insanity99 on 2010-06-03
i normally wait a little while before updating, till the bugs are dealt with. thanks for the link i will check it out.

EDIT: ah removing silent splash seems to have fixed it.

---

