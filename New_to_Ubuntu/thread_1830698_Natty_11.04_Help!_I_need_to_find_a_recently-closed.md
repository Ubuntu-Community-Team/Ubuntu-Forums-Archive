---
title: "Natty 11.04 Help! I need to find a recently-closed document"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by Andavane on 2011-08-22
Oh Help!
I've been working on a document for three hours, and I exited.
As soon as I exited I realised I hadn't noted the path.
I am **so used** in earlier distros to just VIEW RECENT documents and retrieve it that way, however there seems not to be that option in 11.04.

I have **scoured the net and forums** and found nothing!

---

### Post by lmarmisa on 2011-08-22
Log off your account. Then login again selecting Ubuntu Classic. Finally select Places -> Recent Documents.

---

### Post by lmarmisa on 2011-08-22
This is an alternative method. 

The list with your recent documents is located at **~/.local/share/recently-used.xbel** . This is a xml file. Copy it to your desktop and rename its extension to **.xml** . Click twice and the file will be opened with Firefox. Then you will be able to see its contents.

---

### Post by grahammechanical on 2011-08-22
In 11.04 Unity you can click on the Files and Folders lens (icon like a magnifying glass over a sheet of paper with the right top corner folded over) and the dash will appear with icons representing recently opened documents and images and sound files.

Regards.

---

### Post by Andavane on 2011-08-25
Thank you both! :

Yes I have done that and I get the picture attached showing the tree.
How do I associate this file?

> **grahammechanical said:**
> In 11.04 Unity you can click on the Files and Folders lens (icon like a magnifying glass over a sheet of paper with the right top corner folded over) and the dash will appear with icons representing recently opened documents and images and sound files.

Regards.
Wow, doesn't it just? :)
What's more, you can go back over masses of files, far more than you could with the old Recent Documents in places.

Thank you!

---

### Post by lmarmisa on 2011-08-25
Look for lines starting with **"<bookmark href=file:///"**. Those are the recently used documents. This solution is not smart but it works.

Switch to Ubuntu classic is you want to select Places -> Recent Documents.

---

