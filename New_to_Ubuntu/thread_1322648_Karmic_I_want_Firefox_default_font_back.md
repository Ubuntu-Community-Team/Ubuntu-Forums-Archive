---
title: "Karmic: I want Firefox default font back"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by infernus_crusher on 2009-11-11
I just installed ubuntu-restricted-extras and some fonts couldn't install (was trying to connect to archive.canonical.com and it never responded).

To my surprise the fonts on Firefox (e.g. Facebook) had changed to Windows XP style which I didn't like. How do I set it back to the original one?

---

### Post by infernus_crusher on 2009-11-11
Seems to me that the problem is the TTF font that wouldn't install, due to the fact that I couldn't connect to sourceforge or canonical.

---

### Post by masux594 on 2009-11-11
Have u tried to install Ms fonts? .. See [this article]("http://embraceubuntu.com/2005/09/09/installing-microsoft-fonts/")..

Sysc, A

---

### Post by coffeecat on 2009-11-11
> **masux594 said:**
> Have u tried to install Ms fonts?

It sounds to me that some of the MS fonts did install before the problem, and that....

> **infernus_crusher said:**
> To my surprise the fonts on Firefox (e.g. Facebook) had changed to Windows XP style which I didn't like. How do I set it back to the original one?

... webpages that are coded for MS fonts are now displaying (for example) Verdana instead of the default install fallback font.

As an example - whenever I freshly install Ubuntu, the posts in this forum display with the Ubuntu Firefox default of 'serif' - an open source font. But when I installed the MS fonts here in this Karmic install, the text of Ubuntuforums posts displayed in Verdana instead. Which I happen to prefer, but the OP clearly does not.

**infernus_crusher**, if this is the problem, try uninstalling the package ttf-mscorefonts-installer. I don't know whether this will actually uninstall the fonts - I've never tried. If not, you'll have to find the *.ttf files, delete them and run fc-cache. Post back if you need more help.

Of course, this will mean that you won't have things like Times New Roman in Open Office.

---

### Post by infernus_crusher on 2009-11-11
Alright I toyed around with the DNS setting to use OpenDNS and managed to download the ttf installer. Everything's back to where it started now.

---

