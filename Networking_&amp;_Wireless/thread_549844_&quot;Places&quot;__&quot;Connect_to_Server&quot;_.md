---
title: "&quot;Places&quot; | &quot;Connect to Server&quot; | &quot;FTP with login&quot; server opens readonly connection"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by Rene7705 on 2007-09-13
When opening files from that share, which I couldn't even tell to be readonly and isn't readonly in other apps, Text Editor cannot save because it's in readonly mode..

How can I open a readwrite connection to an FTP server (with login)?

---

### Post by Rene7705 on 2007-09-13
solved once before:

[http://ubuntuforums.org/archive/index.php/t-441048.html](http://ubuntuforums.org/archive/index.php/t-441048.html)

Cybolic
May 22nd, 2007, 10:35 PM
You can open gconf-editor (press Alt+F2 and write gconf-editor), go to
apps/gedit-2/preferences/editor/save/writable-vfs-schemes
and add ftp (and ssh) to the list. That should do the trick :) .
It was bugging the hell out of me too ;)




imno this should be standard. the ftp server determines read/write xs, not (for noobs) mysterious gconf settings...

---

