---
title: "Dealing with RAR files"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Tews on 2009-02-04
I downloaded a RAR file but the file type is not supported .. what will I need to extract the files??

---

### Post by Soulcage on 2009-02-04
> **Tews said:**
> I downloaded a RAR file but the file type is not supported .. what will I need to extract the files??

You need to install unrar. You can use "sudo apt-get install unrar" inside a terminal or search in synaptic.

---

### Post by billgoldberg on 2009-02-04
I would use p7zip-full.

Install unrar or p7zip-full, then you can just right-click the file and extract it, using the standard Ubuntu tool.

---

### Post by lswest on 2009-02-04
Also, if you want to create RAR files, you'll need to install the rar package (which, I believe, is in the Medibuntu repo).

---

### Post by Tews on 2009-02-04
> **Soulcage said:**
> You need to install unrar. You can use "sudo apt-get install unrar" inside a terminal or search in synaptic.

Thanks to all .. I knew there was a simple answer :D

---

### Post by ErsinG on 2009-02-04
```
sudo apt-get install rar
``` 

is a solution too ;)

---

### Post by Skrean on 2009-02-04
Install 7-Zip from the Accessories section in Add/Remove Applications.

Once installed you just need to right click the .rar and choose 'Extract Here' and the file will be unrared.

Note:Even if 7-Zip is installed double-clicking on the file will not work.

---

### Post by smfai on 2009-02-14
I want to know if p7zip can deal with .rar ,so why there is a p7zip-rar ?:confused:

---

