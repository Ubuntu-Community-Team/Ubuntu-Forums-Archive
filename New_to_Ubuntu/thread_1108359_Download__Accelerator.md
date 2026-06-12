---
title: "Download  Accelerator"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Wovaki on 2009-03-27
Hello

I am looking for a download accelerator for Ubuntu. I would like one that works with MegaUpload, I tried a couple from the package manager, but I can't get any to work with megaupload.

Thanks

---

### Post by ronocdh on 2009-03-27
I'm not familiar with the service you mention, but have you tried the DownThemAll extension for Firefox? It supports chunking, which can substantially increase download speeds. Also supports pause/resume across sessions (meaning if you quit Firefox and then reboot, your downloads will still be saved as partially complete).

Can also download batches of files off a single page (hence the name).

---

### Post by Rolcol on 2009-03-27
Are you looking for a program that can take different URLs that each download a different section of the same file?  Axel works that way.  It's in the repositories but it's command-line only.  The syntax should be ```
axel http://url1/download.bin http://url2/download.bin
```

It doesn't check if these urls are the same file before the download.

[http://packages.ubuntu.com/intrepid/axel](http://packages.ubuntu.com/intrepid/axel)

---

### Post by sandyd on 2009-03-27
THe problem is probably becuase of the refer code...

install flashgot for firefox

then 
```

sudo apt-get install kget
```
when you click to download something, chose the downloadmanager "kget"

---

### Post by binbash on 2009-03-28
Jdownloader

---

### Post by Wovaki on 2009-03-28
Thanks for the replies!

But I found out that megaupload only supports download accelerators if you buy their premium accounts. :(

Thanks anyways.

---

