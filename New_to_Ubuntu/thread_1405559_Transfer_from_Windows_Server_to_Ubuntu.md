---
title: "Transfer from Windows Server to Ubuntu"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by thesolitaire on 2010-02-12
(First let me apologize for my noobness, I am a Advanced computer user, but when it comes to websites, I am a total noob)

 I am having some issues when it comes to a forums transfer.

I was using Windows server 2003 to run a small web page, with a forum.
Xamp was the Apache interface, the Forums was a PHPBB running with MySQL.

Switching to Ubuntu I am having some issues transfering the Database across.

anyone know where I can find some good reading material on this subject/ have a suggestion?  I am also looking for info on setting up the web page, I have the basics, but don't think I've done it correctly.  Again any direction pointing would be very helpful, I am not averse to reading, but need a place to start.

thanks

---

### Post by mhgsys on 2010-02-12
To be honest, This isn't my cup of tea.

[http://www.google.com/search?btnG=1&pws=0&q=lamp+server](http://www.google.com/search?btnG=1&pws=0&q=lamp+server)

---

### Post by The Cog on 2010-02-13
I would have thought that copying the MySQL database files might work, but maybe not. The best way to do this is to use the proper dump and load programs. You can make a complete dump of the MySQL database into a text file with the command **mysqldump**:
[http://www.patrickpatoray.com/index.php?Page=30](http://www.patrickpatoray.com/index.php?Page=30)
[http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html)

I have had need of this occasionally, on databases of a few GB. It's not lightning fast, but it worked for me. You can do the restore to a freshly installed MySQL and when it's finished, the whole database is there. Magic!

---

