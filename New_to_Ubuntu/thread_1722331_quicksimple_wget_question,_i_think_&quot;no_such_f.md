---
title: "quick/simple wget question, i think: &quot;no such file or directory&quot;"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by earthpigg on 2011-04-05
```
[chris: ~/Desktop/folder backup]$ wget http://www.validwebsite.net/file.swf
--2011-04-05 14:29:30--  http://www.validwebsite.net/file.swf
Resolving www.stormfx.net... 72.XXX.XXX.XXX
Connecting to www.stormfx.net|72.XXX.XXX.XXX|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 61194111 (58M) [application/x-shockwave-flash]
Saving to: `file.swf'

100%[======================================>] 61,194,111   535K/s   in 2m 57s  

utime(file.swf): No such file or directory
2011-04-05 14:32:29 (337 KB/s) - `file.swf' saved [61194111/61194111]

[chris: ~/Desktop/folder backup]$ ls
[chris: ~/Desktop/folder backup]$ 
(snip)
[chris: ~]$ ls -AR | grep file.swf

```

given the length of time it took, it downloaded to somewhere. it seems to have been misplaced. i can just do this using firefox's file -> save page as, but I'd like to know what went wrong with wget.

---

### Post by TeoBigusGeekus on 2011-04-05
In order for wget to save a file, you need to use the -O option:
```
wget http://www.validwebsite.net/file.swf -O file.swf
```
Without the -O option, your terminal downloaded the file (probably in /tmp or something), tried to "show" it, failed miserably and deleted the temporary swf file.

---

### Post by tgm4883 on 2011-04-05
> **TeoBigusGeekus said:**
> In order for wget to save a file, you need to use the -O option:
```
wget http://www.validwebsite.net/file.swf -O file.swf
```
Without the -O option, your terminal downloaded the file (probably in /tmp or something), tried to "show" it, failed miserably and deleted the temporary swf file.

Not true, by default it saves it to the same directory. Not sure why it didn't for the op though

---

### Post by earthpigg on 2011-04-05
yes, i generally don't use -O with wget and it hasn't given me problems in the past.

this looks to be the culprit, but i have no idea what it means.

```
utime(file.swf): No such file or directory
```

it isn't the end of the world if no one can figure out why it didn't work, but it would be nice to know.

---

