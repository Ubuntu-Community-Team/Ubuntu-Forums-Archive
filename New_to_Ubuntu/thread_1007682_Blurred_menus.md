---
title: "Blurred menus"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Syron on 2008-12-10
While running MUSHclient through WINE today I noticed that the menus were very blurred. It looked somewhat like someone hand scribbled on them. Below is a screenshot of the WINE config menu when I opened it to see what might be the problem.

[IMG]http://i178.photobucket.com/albums/w252/Ghostofgod/Screenshot.png?t=1228948768[/IMG]

---

### Post by doctorbighands on 2008-12-10
This is a known bug. See here: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/294676](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/294676)

I didn't see a workaround, but if you google more than I did, you may find one.

---

### Post by Kellemora on 2008-12-10
Hi Syron

Did you recently install anything that included fonts or installed duplicate fonts in two different places on your computer?

Don't know if this is your problem or not, but it's what caused it for others!

For example, they installed msttcorefonts AFTER they already had one of those fonts in another folder and whammo things in Wine became unreadable and producing the same image you just posted.

There are other bugs that cause the same thing to happen, so, if it's one of those, you're up that proverbial creek without a paddle, as far as what I know to help goes!

TTUL
Gary

---

### Post by Syron on 2008-12-10
The only thing that I can think of recently installing were the most recent released 8.10 updates. I'll start researching it though.

---

