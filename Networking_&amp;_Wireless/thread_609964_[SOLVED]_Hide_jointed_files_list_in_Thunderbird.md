---
title: "[SOLVED] Hide jointed files list in Thunderbird"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by alexisj on 2007-11-11
Is it possible to hide the list of jointed files (or part of emails when you're receiving a digest mail from a mailing-list)?

It is possible to click and hide manualy this bar for each mail but by default, I don't know.

Have you some way to hide it by default?

Tx :)

Check this snapshot to understand what is the "problem":

[IMG]http://www.alexis.lautre.net/ubuntu/thunderbird.jpg[/IMG]



This topic in french:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1313793](http://forum.ubuntu-fr.org/viewtopic.php?pid=1313793)

---

### Post by alexisj on 2007-11-13
I answer to myself to explain how to fix this problem easily.


1. Create a text file named *userChrome.css* in this folder: */home/-user-/.mozilla-thunderbird/-crypted-profile-name-.default/chrome/*
2. Add in it this lines:

```
/* Attachment pane at bottom of message window */
 #attachmentView {
   -moz-appearance: none !important;
   height: 2px !important;
   overflow: auto !important; }
```

If  *userChrome.css*  yet exist, you can just add this lines (or editing it if they exists)

Source:[http://kb.mozillazine.org/Attachment_pane_height_-_Thunderbird]("http://kb.mozillazine.org/Attachment_pane_height_-_Thunderbird")

---

