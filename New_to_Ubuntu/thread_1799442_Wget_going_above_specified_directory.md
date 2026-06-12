---
title: "Wget going above specified directory"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by rogueit on 2011-07-07
I am trying to understand Wget. I would like to download a mp3 from a website. when I tell wget to go to this website and the folder it successfully grabs the file but then moves up a level and trys to grab a file I don't want. How can this be avoided.

```
wget --http-user=myUser --http-password=myPass -A  .mp3 -r  --no-parent "http://website.yahoo.com:19766/holdingstuff/targetdir"
```It successfully gets the mp3 from targetdir, but then grabs another mp3 from 
[http://website.yahoo.com:19766/holdingstuff/anotherdir](http://website.yahoo.com:19766/holdingstuff/anotherdir)

GNU Wget 1.12
ubuntu 11.04

---

### Post by jtarin on 2011-07-07
Posiibly [Recursive Accept/Reject Options]("http://www.gnu.org/software/wget/manual/wget.html#Recursive-Accept_002fReject-Options")

---

