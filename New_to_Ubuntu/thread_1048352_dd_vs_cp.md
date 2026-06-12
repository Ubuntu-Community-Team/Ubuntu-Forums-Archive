---
title: "dd vs cp"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Gwasanaethau on 2009-01-23
Hi everyone.

I was wondering, is it safe to use the 'dd' command for file transfer/copying instead of 'cp'? I have some DVD+RWs that are a bit old and mashed, and I want to see how much space I can actually use on them.

Cheers!

---

### Post by cmnorton on 2009-01-24
To the best of my knowledge, there is nothing wrong with pulling files from a dvd using dd. dd give you the ability to convert and copy, and is one way to image.

---

### Post by Gwasanaethau on 2009-01-26
Lovely, that's great, thanks a mill. I sort of thought that was the case, but I heard somewhere that copying files on a single filesystem using dd 'clobbers' it. That sounded dangerous, so I just wanted to get a second opinion before I tried anything. ;)

Thanks again.

---

### Post by Rolcol on 2009-01-26
dd is more of a "dirty" utility in the sense that it lets you set more specific settings without being as clean as cp.  I think both cp and dd will result in the same image file if you use them to clone a dvd.  I'd personally use dd for a cd image and pipe it out into bzip2 for compression before saving it.

---

### Post by hyper_ch on 2009-01-26
dd reads a block device, cp reads file. Why would that make dd "dirty"?

---

