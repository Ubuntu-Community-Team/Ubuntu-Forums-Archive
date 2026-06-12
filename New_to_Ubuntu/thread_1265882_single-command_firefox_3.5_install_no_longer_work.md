---
title: "single-command firefox 3.5 install no longer work"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by stevepoppers on 2009-09-14
```
wget -O - http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2 | tar xj -C ~

```
No longer seems to work. The output is
```
-2009-09-14 00:14:40--  http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2
Resolving releases.mozilla.org... 204.246.0.136, 155.98.64.83, 156.56.247.196, ...
Connecting to releases.mozilla.org|204.246.0.136|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-09-14 00:14:40 ERROR 404: Not Found.


bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors

```

I'm thinking that that means that the download link no longer works for some reason. Am I right? And why is there no debian package to make this easy?

---

### Post by jualin on 2009-09-14
Try
[HTML]wget -O - http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/en-US/firefox-3.5.3.tar.bz2 | tar xj -C ~[/HTML]

---

### Post by stevepoppers on 2009-09-21
That works. Thanks.

---

