---
title: "wifi tool to measure signal quality"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Tex-Twil on 2007-07-24
Hello,
I'm looking for a good tool to measure a wifi signal quality.  An equivalent of the windows NetStumbler would fit.

Thank you.

---

### Post by kevdog on 2007-07-24
How about swscanner??  Its in the repositories.  I dont think it works in Feisty unless you compile from svn source.  If edgy or below works without a problem.

---

### Post by Tex-Twil on 2007-07-24
Hi,
yes, swscan crashes on faisty. I'll try to recompile it.

---

### Post by Tex-Twil on 2007-07-24
hmmm I can't access the SVN server :s

---

### Post by kevdog on 2007-07-24
I had to download the tar.gz package, since typing svn at the command line wouldn't work.  Not the most elegant solution I know, but it was the only thing that worked for me.  Here is the link:
[http://websvn.swscanner.org/dl.php?repname=swscanner&path=%2Ftrunk%2F&rev=0&isdir=1](http://websvn.swscanner.org/dl.php?repname=swscanner&path=%2Ftrunk%2F&rev=0&isdir=1)

---

### Post by Tex-Twil on 2007-07-24
ok thanks,
when I try to configure those it says :

> 
configure: error: iwlib.h not found. Missing wireless-tools??


but I have wireless-tools installed

---

### Post by Tex-Twil on 2007-10-22
FYI,
the** iwlib.h** error is solved by installing 

> 
sudo apt-get install libiw-dev


cheers

---

