---
title: "long file names and their 8-chars versions"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by motumboe on 2007-04-11
Hello,
 we have a ubuntu-server edgy  file server (file system of the shared files: ext3) and a win xp client with an old program that shows up the 8-char version of long file names.
While in windows the association is as follows:
longfilename -> LONGFI~1
longfilename2 -> LONGFI~2

...in ext3 the association is not so 'straight-on' and this forces my colleague to guess the names... 

Is there a way to force a windows-like association between long file names and their short version?

Thanks in advance.
Regards,
 Marco

---

### Post by motumboe on 2007-04-12
It's a Samba issue. Simply add 
[FONT="Courier New"]mangling method = hash[/FONT]
in the [global] section of smb.conf.

Cheers
 Marco

---

