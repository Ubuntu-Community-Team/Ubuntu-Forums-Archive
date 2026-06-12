---
title: "[SOLVED] Extreme Compression of PDF File"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by lhb1142 on 2008-12-26
I have a PDF file of 9.9 MB which I need to compress down to at most 4.9 MB (better than 50%).

I have tried the various terminal commands I have found on this forum as well as the PeaZip utility but the best I can accomplish is to get the file down to 5.6 MB. This is not sufficient for my needs.

I would like to know if there is an "adjustable" compression program or terminal command which will allow me to set the exact level of compression.

I would prefer to be able to create a self-extracting compressed file but this is not absolutely necessary. A ZIP or .tar file would do.

Can anyone help me?

---

### Post by ercferret18 on 2008-12-26
would it work to split the file into two parts, and then transfer them both and recombine them?

---

### Post by lhb1142 on 2008-12-26
Thanks for your quick reply but, sorry, it is not possible to split the file. It must remain intact but heavily compressed.

---

### Post by ercferret18 on 2008-12-26
if you have windows, you could try 7zip and choose "Ultra" in the compression modes. or you could try compressing it, then compressing the compressed file, and so on, until you get it down far enough.

---

### Post by jamesrl on 2008-12-26
Have you tried

```
gzip --best my.pdf
```

Also is this a pdf you are making?  It makes significantly more sense to do a slightly lossy compression of image data prior to making the pdf (e.g., save images as jpeg) rather than try to compress them embedded in a pdf.

The analogy is similar to mp3 compression.  If you start with a mp3 created at 256 kbps and compress it using gzip type tools, you'll gain a few percent (I just tried gzip --best and got ~3% ... not much).  If you re-encode the mp3 at say 128kbps or 64kbps (or variable bit encoding), you'll reduce it by half or a quarter with slight loss of quality.

---

### Post by kaibob on 2008-12-26
> **ercferret18 said:**
> if you have windows, you could try 7zip and choose "Ultra" in the compression modes. or you could try compressing it, then compressing the compressed file, and so on, until you get it down far enough.

If you look at the "comparison of efficiency" table on the following page, you'll find that 7-zip generally compresses the most. Bzip2 does almost as well and is available for Linux. 

[http://en.wikipedia.org/wiki/Comparison_of_file_archivers](http://en.wikipedia.org/wiki/Comparison_of_file_archivers)

If that doesn't do the job, you can reduce the size of the PDF with Ghostscript.

---

### Post by lhb1142 on 2008-12-26
I want to thank everyone here who has responded to me. The various suggestions individually did not completely solve my problem but, taken together, they did.

I used PeaZip on this file with 7Z compression and adjusted the file to the Custom Size - Attachment Limit 5 MB and this worked.

By the way, PeaZip is a very good archiving program - and 7Z IS available in it along with BZip2, ZIP, and quite a few other compression codecs.

---

