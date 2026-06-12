---
title: "Movies are jitterbugging while playing /w ATI drivers installed"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by interp on 2009-02-23
Movies are jitterbugging while playing /w ATI drivers installed

When I remove the ATI drivers movies play fine.  Anyone else had this problem?

2900XT 512mb
19" was running it @ 1280x1024 | 75Hz

help please?

---

### Post by hobo89 on 2009-02-23
Do you have Compiz running also? It's a known bug with Compiz and ATI drivers. You need to disable Compiz/desktop effects whilst watching video files.

---

### Post by interp on 2009-02-23
That's probably it, thanks! :)

---

### Post by zika on 2009-02-23
System->Preferences->MultimediaSystemsSelector->Video->X11(no Xv) and You can keep compiz ... ;)

---

### Post by interp on 2009-02-23
Compiz wasn't even installed and I don't have that option in my menu either :S 

Still stuck :/ 

Anymore ideas or anyway to edit the cfg?

---

### Post by zika on 2009-02-24
Alt-F2->gstreamer-properties->Video->X11(no Xv)

(if that does not give You result tweaking is possible but be aware of [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593)

to get MultimediaSystemsSelector: System->Preferences->MainMenu->Preferences->check MultimediaSystemsSelector

---

### Post by hobo89 on 2009-02-24
> **interp said:**
> Compiz wasn't even installed and I don't have that option in my menu either :S 

Still stuck :/ 

Anymore ideas or anyway to edit the cfg?

It could also just be Visual Effects, under the Appearance Preferences. Any setting but 'None' will cause the problems.

---

### Post by zika on 2009-02-24
> **hobo89 said:**
> It could also just be Visual Effects, under the Appearance Preferences. Any setting but 'None' will cause the problems.
that can be solved by choosing X11 as Video output and keeping video effect people like. (I don't, but that's my problem ... ;))

---

