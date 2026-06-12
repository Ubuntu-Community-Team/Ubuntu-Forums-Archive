---
title: "Ubuntu 10.04 Truecrypt 7.0 Where is the auto-dismount on screensaver option?"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by rocksockdoc on 2010-09-04
I just moved over from the WinXP world to Ubuntu 10.04 on a Lenovo Thinkpad. 

Truecrypt 7.0 on Ubuntu does not seem to have the option that Windows had of automatically unmounting all mounted encrypted volumes upon screensaver activation.

Since everyone must want this feature, there must be an existing "trick" or setup that causes automatic dismounting of mounted volumes when using Truecrypt.

What is that trick to autodismount Truecrypt encrypted volumes on screensaver?


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=168449&stc=1&d=1283592618[/IMG]

---

### Post by rocksockdoc on 2010-09-08
Am I to conclude this Windows option of auto dismounting upon screensaver does not exist on the Ubuntu version of Truecrypt?

---

### Post by rotave on 2010-09-08
Yep. I couldn't find that option. You could try "ScramDisk 4 Linux". It supports truecrypt drives up to version 6.3a. It gives you the option of setting a container inactivity timeout option where it will auto dismount after a user set period of inactivity.

---

### Post by rocksockdoc on 2010-09-09
> **rotave said:**
> You could try "ScramDisk 4 Linux"

Thanks for answering. I knew there had to be some way of auto-dismounting because it's something that already existed (on the PC side) and it's something everyone would want.

I'll check into ScramDisk (but I see I need an older revision of Truecrypt) and it seems to be deprecated in favor of Sourceforge "ScramDisk 4 Linux" according to a recent Wikipedia search (see screenshot below).

Thanks!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189856&stc=1&d=1303625749[/IMG]

---

### Post by rocksockdoc on 2011-04-24
> **rocksockdoc said:**
> I'll check into ScramDisk

Drat. 

ScramDisk for Linux (aka SDL4), wasn't in the Ubuntu Software Center nor in the Synaptics Package Manager, so I had to go to the developer's web site for the installation package.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189867&stc=1&d=1303629437[/IMG]

Unfortunately, SDL4, from Sourceforge, failed to load into a native Ubuntu 10.04 installation for some reason. :(
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189868&stc=1&d=1303629437[/IMG]

---

