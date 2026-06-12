---
title: "Scanning in Image Scan for Linux"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by daniell59 on 2010-08-12
I would like to scan a book. How can I do it with the above program?
I don't want each page to be a separate file.

Thanks

---

### Post by Paul820 on 2010-08-12
Does the manual not suggest anything? If you google for "image scan linux", there is a pdf you can download.

---

### Post by daniell59 on 2010-08-12
> **Paul820 said:**
> Does the manual not suggest anything? If you google for "image scan linux", there is a pdf you can download.

Thanks, I will do as you suggested.

---

### Post by SoFl W on 2010-08-12
xsane has a multi-page option, or you can use pdfjoin to put each page together.

---

### Post by daniell59 on 2010-08-12
> **SoFl W said:**
> xsane has a multi-page option, or you can use pdfjoin to put each page together.

Thanks, I have that installed.

---

### Post by lavinog on 2010-08-12
I find it to be quicker to scan each page to a file first, then join the files afterwards.  This way if there was an issue with one page, you don't need to start over.


Also, you can try djvu if you want to make the scans save a lot of space:
You will need to install djvulibre-bin first.

For color scans you can scan to jpeg first, then convert the scanned images to djvu
```

c44 scan0001.jpg page0001.djvu

```
If you have a bunch of files you wish to convert:
```

for f in *jpg ;do echo $f ; c44 $f ${f%.jpg}.djvu ;done

```

If you want bitonal use cjb2 and the input file needs to be a pbm file.

When you are done you can join all of the files with djvm:
```

djvm -c book.djvu page*.djvu

```

---

### Post by SoFl W on 2010-08-12
> **lavinog said:**
> I find it to be quicker to scan each page to a file first, then join the files afterwards.  This way if there was an issue with one page, you don't need to start over.

xsane's multi-page option allows you to move pages around, delete or re-scan a page.  (Actually not a re-scan but a new scan and you move it to the original place)

**[Here is]("http://ubuntulinuxtipstricks.blogspot.com/2009/02/scanning-multipage-documents-in-xsane.html")** a note on how to use multi-page along with a note on scanning to PDFs using gscan2pdf.

---

### Post by macogw on 2010-08-12
> **SoFl W said:**
> xsane's multi-page option allows you to move pages around, delete or re-scan a page.  (Actually not a re-scan but a new scan and you move it to the original place)

**[Here is]("http://ubuntulinuxtipstricks.blogspot.com/2009/02/scanning-multipage-documents-in-xsane.html")** a note on how to use multi-page along with a note on scanning to PDFs using gscan2pdf.

That's my blog, but nowadays I **highly** recommend Simple Scan.  Click a button, and it scans the page.  Click the button again, and it scans the next page.  Click "Save" and you get a multi-page PDF.

---

### Post by SoFl W on 2010-08-13
Thank you for that tutorial, during some update of [libsane package]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476") no longer supported my old scanner and I was going back to Windows to scan documents.  I eventually purchased a new all-in-one and used your page to refresh my memory on multi-page scanning.  I like Xsane, and Epson's Image Scan, I removed Simple Scan from the menu after a few problems.

---

### Post by mebunto on 2011-06-22
Simple scan works wonderfully!  Thanks

---

