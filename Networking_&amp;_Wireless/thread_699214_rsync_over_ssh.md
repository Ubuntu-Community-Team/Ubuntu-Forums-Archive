---
title: "rsync over ssh"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by fluoblack on 2008-02-17
Hi everyone!
I decided to use rsync to backup my laptop over ssh, but I'm having a hard time writing the right command. 

I want to copy my files from my laptop (media/to/be/backedup) to my server (IP.IP...). '
The server must keep an uncompressed copy of my laptop.
After the fisrt full backup, rsync must erase all files that are not present anymore on my laptop and copy only the files that have been modified or added
finally rsync has to be recursive and keep the directory hirearchy

I tried this simple command that I'm sure is wrong:

rsync -nrv /media/to/be/backedup -e [email]me@IP.IP.IP.IP[/email]:/media/backup 

A little hint would be much appreciated.

---

### Post by RandomJoe on 2008-02-17
I use an extension of the following to do a full backup:

```
rsync -av --delete --rsh=ssh /stuff/to/backup/ user@server:/where/to/put/it/
```

The "--rsh=ssh" may not be needed anymore, but I wrote my script a long time ago.  My extensions are primarily a bunch of "--excludes" to not backup certain directories (kinda hard to get /proc for some reason! :p )

The trailing slashes on the paths can be significant.  For instance, "/stuff/to/backup/" means rsync grabs the stuff in the "backup" directory.  But "/stuff/to/backup" means it will grab the directory itself, recreating it on the other end.

---

