---
title: "inconsistency df &lt;=&gt; du"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by itmozart on 2009-08-28
I have a mounted drive, whose df -h output is:

/dev/sda7              19G   18G     0 100% /var

But when I go to the directory, and run du -ch, I get:

1.1G    total

How do I found what's taking so much space? I can't find where those other ~17 are.
The environment is headless, so no aid from graphical tools :-(

Saverio

---

### Post by DaithiF on 2009-08-28
Hi,
This could be an open-file-descriptor issue.  If a file is deleted or moved while it is being accessed by another process, the space it takes up will not reported as free by df unless/until the process which is using the file exits.  However the file will not be found by du, and so you get a discrepancy where df reports greater usage than you can explain by running du.

A reboot may be the quickest way to rectify this providing you can bring down the server.

Alternatively, you can use lsof to search for open but deleted files
```
cd /var
sudo lsof -s | grep DEL | sort -rnk 7,7 

```
For a  17GB diff, there are likely a few very large files that should stand out.  The 2nd column shows the process id using the file -- killing the process will also release the space.

---

### Post by slakkie on 2009-08-28
[http://www.cyberciti.biz/tips/freebsd-why-command-df-and-du-reports-different-output.html](http://www.cyberciti.biz/tips/freebsd-why-command-df-and-du-reports-different-output.html)

[http://lists.debian.org/debian-isp/2002/05/msg00046.html](http://lists.debian.org/debian-isp/2002/05/msg00046.html)

---

### Post by itmozart on 2009-08-28
Spot-on, many thanks!!
I had several very very long running apache and ssh processes stacking (deleted) logging upon logging.

Saverio

---

