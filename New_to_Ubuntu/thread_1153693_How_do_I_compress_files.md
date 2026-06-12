---
title: "How do I compress files"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-05-09
I want to make a file as small as possible. I heard that it is possible to create extremely compressed files, is this true? If so, how do I do it?

I looked at the graphical archive manager and it doesn't seem to have an option to change the output size or compression level. Is there a way to do this?

---

### Post by Toshubu on 2009-05-09
Use gzip, from the command line.  (Try:  man gzip, or man zip for more info)

---

### Post by logos34 on 2009-05-09
bzip (.bz2) and 7zip (.7z) will make even smaller archives than gzip, but they take longer

---

### Post by Operan on 2009-05-09
Install p7zip-full in Synaptic to compress to  7zip format in Archive Manager.

---

### Post by nhasian on 2009-05-09
the type of file you are compressing makes a big difference on how much it can be compressed.  for example text, word processor and spreadsheets compress really well but audio and videos do not.

---

### Post by mcduck on 2009-05-09
> **nhasian said:**
> the type of file you are compressing makes a big difference on how much it can be compressed.  for example text, word processor and spreadsheets compress really well but audio and videos do not.

..and of course the reason for this is that audio and video are already in compressed formats.

Anyway, pretty much every archiving app already compresses your data as much as it can. Your actual result depends on what your data is, and what format are you compressing it into.

---

### Post by Sup3r3g0 on 2009-05-09
Thanks everbody for the help

---

### Post by durand on 2009-05-09
With 7zip, using extreme compression will take hours for even a small file.

---

