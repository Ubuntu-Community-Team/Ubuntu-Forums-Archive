---
title: "Where to Put Man Files?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by azurepancake on 2009-01-09
Awhile ago, I made a very simple BASH script to use at work. I worked a technical support position at a web-hosting company and often had to use 'whois' and 'dig' with many of it's options. So I made a script called 'lazy', which did a whois lookup and dug at a domains A records, MX records, NS records and would try an 'axfr' if possible.

So I've put it in my '/usr/local/bin' directory so I can execute it from anywhere, and just for kicks I want to make a man file for it. However, I'm not too sure where to put the guy. I've tried putting it in the directory '/usr/local/man/man1' and called it lazy. Its basically just a text file stating how to use the script.

Right now it just doesn't seem to work:

```

tristan@panzerkunst:~$ ls -la /usr/local/man/man1
total 12
drwxrwxrwx 2 root    root    4096 2009-01-09 13:35 .
drwxr-xr-x 3 root    root    4096 2009-01-09 13:31 ..
-rwxrwxrwx 1 tristan tristan  579 2009-01-09 13:35 lazy
tristan@panzerkunst:~$ man lazy
No manual entry for lazy
tristan@panzerkunst:~$ whereis -m lazy
lazy:

```

I've noticed that when I search the man files of other installed commands, their man files are compress as GunZip files:

```

tristan@panzerkunst:~$ whereis -m conky
conky: /usr/share/man/man1/conky.1.gz

```

Perhaps this is required step?

I'm just not sure if I need to put it in a different location, name it something special or what. If anyone has any advice, I would greatly appreciate it.

Thank you! :)

---

### Post by Dedoimedo on 2009-01-09
Try rebuilding the database with man --update.
Dedoimedo

---

