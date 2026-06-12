---
title: "CUPS-PDF - choose output folder"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by I2k4 on 2010-11-30
As a habit, I print _everything_ to PDF then decide if/when hard copy is needed.  In XP, my PDF virtual printer brings up a dialog box to choose the output directory.  I was very happy to find Ubuntu also supports printing to PDF with CUPS-PDF, but it specifies output to a folder called "PDF" and offers no alternative.  

I found a three or four year old site offering some terminal commands to change that directory, e.g. to my DropBox (the Google results on this topic all seem to be several years old).  At the bottom of the page that blogger says there's some Linux "issue" that prevents a dialog box to choose output, but the URL to explain that issue doesn't work.  

Now it's been a few years, I'm wondering if there is a fix to whatever was preventing a dialog selection of the output folder for CUPS-PDF, or installing some other software for  this.  Most of the time this comes up when I print out of browsers, FireFox or Chromium, which do not natively print to PDF.  Any help appreciated.

---

### Post by Wobblybob on 2010-11-30
can't help with cups pdf but do you know that [in Gnome at least] if you hit the print button then select the [Print to file] option, you can change the radio button from .ps to .pdf and then select a destination for the print.

---

### Post by redbook4574 on 2010-11-30
> **I2k4 said:**
> As a habit, I print _everything_ to PDF then decide if/when hard copy is needed.  In XP, my PDF virtual printer brings up a dialog box to choose the output directory.  I was very happy to find Ubuntu also supports printing to PDF with CUPS-PDF, but it specifies output to a folder called "PDF" and offers no alternative.  

I found a three or four year old site offering some terminal commands to change that directory, e.g. to my DropBox (the Google results on this topic all seem to be several years old).  At the bottom of the page that blogger says there's some Linux "issue" that prevents a dialog box to choose output, but the URL to explain that issue doesn't work.  

Now it's been a few years, I'm wondering if there is a fix to whatever was preventing a dialog selection of the output folder for CUPS-PDF, or installing some other software for  this.  Most of the time this comes up when I print out of browsers, FireFox or Chromium, which do not natively print to PDF.  Any help appreciated.

I use print to file, it will give you the option of PDF or PS (postsript) and the option of where to save.

---

### Post by I2k4 on 2010-11-30
Thanks, that does it.  Never woulda thunk it.

---

### Post by oldmankit on 2010-11-30
There definitely is a way to change the pdf output folder, I did it before.  It's a little tricky though because apparmor has a builtin profile which only allows output to ~/pdf.  I spent a while trying to fix it but gave up, and just disabled apparmor if I ever needed to print through cups-pdf.

Retrospectively, it would be better to put up with having ~/PDF. If you don't want to see it in nautlilus, just do:

```
echo 'PDF' >> ~/.hidden
```But for most programs (e.g. firefox) yes just print to file and then change output to pdf works fine!

---

