---
title: "How to Download a File in Parts ??"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by katsy on 2010-10-18
I have a large file,say around 700mb.I'd like to download this in parts of 10mb,using some command line tools(wget,cURL ?) ..and then put the parts back together using cat.  The reason i'd like to do this,is cuz my proxy server doesnt allow files larger than 10mb.  Please assist.

---

### Post by blueabysm on 2010-10-18
Google "Wxdownload Fast"&#12290;
This software may be helpful.
the following image is a snapshot. You can see that, it has a function named "Segmented Download".
[IMG]http://dfast.sourceforge.net/images/linux-new.png[/IMG]

Good Luck.

---

### Post by ankspo71 on 2010-10-18
Hi,
Here is an article that shows what you want to do from the terminal.
[http://linuxhelp.blogspot.com/2007/03/tip-download-accelerator-for-linux.html](http://linuxhelp.blogspot.com/2007/03/tip-download-accelerator-for-linux.html) . Interesting stuff. I might one day try it.

Oh yeah... the article demonstrates downloading the large file from multiple locations (in parts), but it should also work in parts from the same location too.

Hope this helps.

---

### Post by ankspo71 on 2010-10-18
Hi again,

If you ever need to download Ubuntu, then the metalink downloads might make this easier you - if your proxy doesn't support torrent downloading. Metalink files (similar to torrent files in a sense) are designed to download the file from multiple web urls. Here is a list of applications that support downloading from metalinks: [http://www.metalinker.org/implementation.html](http://www.metalinker.org/implementation.html)
Be sure to tell your downloader manager to use metalink and download the files in many multiple parts. The firefox addon called downthemall has the option to download from metalinks.

All of the Ubuntu mirrors have files like this: 
ubuntu-10.10-desktop-i386.metalink 
Those would be the one to try.

Too bad metalink downloads aren't very popular yet.:(
[http://www.metalinker.org/samples/ubuntu/](http://www.metalinker.org/samples/ubuntu/)
[http://www.metalinker.org/](http://www.metalinker.org/)
[http://en.wikipedia.org/wiki/Metalink](http://en.wikipedia.org/wiki/Metalink)

---

