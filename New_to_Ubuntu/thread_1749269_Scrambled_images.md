---
title: "Scrambled images"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Walkar on 2011-05-04
A few weeks ago I noticed that, when opening a PDF and scrolling down, the image would become all scrambled. Today, while I was doing the same thing, the entire screen became scrambled, and now I can't even read the PDF, it scrambles so often. It did it on different PDFs, so it's not the file, and it's done it on both Firefox and the Document Viewer program, so I don't think it's just the programs.

Can someone help? Thank you very much in advance.

I'm running Ubuntu 10.10, at 1366x768 resolution. If there's any other information I can include to assist, please let me know.

Screenshots:
[http://i56.tinypic.com/208ir2f.png](http://i56.tinypic.com/208ir2f.png)
[http://i56.tinypic.com/2qvxli9.png](http://i56.tinypic.com/2qvxli9.png)

---

### Post by yetiman64 on 2011-05-04
What is your video card NVidia, ATI etc and model if your know it ? 
```
lspci | grep VGA
``` in a terminal will show your video card details.

Do you have proprietary drivers enabled ? You can look in System > Administration > Hardware Drivers, to check this.

Do you get video tearing when you play video files as well ?

---

