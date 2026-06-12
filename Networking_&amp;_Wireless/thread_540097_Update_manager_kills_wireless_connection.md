---
title: "Update manager kills wireless connection"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by bogoliubov on 2007-09-01
Hello. Whenever I run Update-Manager using a wireless connection, the connection is lost and I have to restart the router. I have experienced this in Edgy and Feisty on an iBook G4, and now in Fiesty on a Clevo with Intel wireless. 

This is really weird! What can I do about it??

---

### Post by bogoliubov on 2007-09-01
Bump...

---

### Post by bobatronx on 2007-11-14
I realize you posted this quite awhile ago, but I was running into the same problem; and I believe I found a solution.  There is a sticky thread at the top of ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

This should answer your questions.

My situation was that I was running a Linksys WMP54G wireless card, which should be supported by Ubuntu.  The driver set, however, was just slightly newer than what Ubuntu supports.  They support v 4.0 and these are 4.1.  The solution was to use ndiswrapper, which is explained in the above link.  Ndiswrapper will allow you to install the windows drivers that came with your wireless card.  First, however, you need to blacklist any drivers that ubuntu may be trying to use automatically for your wireless card.  This is all explained in the above link, just make sure you blacklist the appropriate drivers for your specific card.  I'm fairly new to linux, so this is probably all the advice I can give you.

---

