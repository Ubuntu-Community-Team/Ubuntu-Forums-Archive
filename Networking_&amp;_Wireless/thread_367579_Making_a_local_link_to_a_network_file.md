---
title: "Making a local link to a network file?"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by mjpatey on 2007-02-22
How do I make a local link to a file on my network?  I want to create a link on the Desktop to a spreadsheet file on another computer (which is running Windows).  I can access and edit the file by navigating to it on the network, but I want a shortcut to it on my Desktop.

I tried right-clicking it in the file browser and selecting "make link", but it wouldn't allow me to create a link there, because it's on my other (Windows) computer.

Thanks for any help you may have!

-Mark

---

### Post by Jussi Kukkonen on 2007-02-22
right-click on desktop, select  "create launcher", set type to "file"  -- the rest should be self explanatory.

The above will create a desktop link. To create a real symbolic link that'll work everywhere look at the *ln* command (see *man ln*)

---

