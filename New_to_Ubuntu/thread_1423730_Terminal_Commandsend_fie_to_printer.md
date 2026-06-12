---
title: "Terminal Command:send fie to printer?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-03-07
Hi everyone,

Suppose I want to print a file thru the command line.

I googled an older thread on here, which suggested getting LPR 
from the repo. 

I apt-get install lpr and got:

The following packages will be REMOVED:
  cups-bsd ubuntu-desktop
The following NEW packages will be installed:
  lpr

So I typed 'no' since that seemed like it would mess up my now working perfectly printer setup.

Will installing LPR change my whole print setup, and/or is there a way to pipe a file
to the CUPS server....note that the idea of piping and other shell commands is still pretty new to me.

thanks !
wbg

---

### Post by wojox on 2010-03-07
This is how I do it:

```
cat MyFile.txt > /dev/lp
```

Even if you pipe it you still need lpr:

```
cat MyFile.txt | lpr
```

---

### Post by patchwork on 2010-03-07
Can you do the same thing with lp instead of lpr?   I've never tried this, but the man pages for each seem eerily similar.

---

### Post by wannabegeek on 2010-03-07
Thanks patch, I tried your suggestion:

> **wojox said:**
> This is how I do it:

```
cat MyFile.txt > /dev/lp
```



even with sudo i got 'permission denied /dev/lp'

wbg

---

### Post by Bachstelze on 2010-03-07
> **wannabegeek said:**
> 
even with sudo i got 'permission denied /dev/lp'

wbg

What does [font=monospace]ls -l /dev/lp[/font] say?

---

### Post by wannabegeek on 2010-03-07
hah.../dev/lp does not exist...

hmm....

---

### Post by HermanAB on 2010-03-07
As far as I can figure, it is not really lp or lpr anymore.  These are merely little compatibility programs that actually talk to CUPS, in order  print.

---

### Post by wannabegeek on 2010-03-07
lpr foo

that was it !

I didn't install the lpr package from synaptics either....

I love terminal...

---

