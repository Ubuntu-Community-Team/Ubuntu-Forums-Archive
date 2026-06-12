---
title: "Firefox extremely slow to print web page"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mmasroorali on 2009-12-27
Dear All,
This issue is very disturbing.

We are trying to print some reports generated in html. The reports contain simple tables without anything special. There is no image, no water mark, nothing. When printed on A4 pages, we need around 150 sheets. The html file size is around 1.5M.

When we try to print from Ubuntu in Firefox, the printing takes a lot of time. First, it says, Preparing..., takes considerable time and freezes all other tabs, then goes to Printing..., again takes a long time, then it starts printing. But there is an appreciable wait between pages. When checked in queue, we find that the print file size is several MB. And when printed as a file, the .pdf file comes to around 20MB. 

When we try to print the same page from Opera or Epiphany, printing is completed almost instantaneously, and the print file size, if printed as a pdf file, is about the same as original html file.

Please let me know what I can check. I need to use Firefox rather than other browsers for a special reason.

Thanks in advance.

---

### Post by mörgæs on 2009-12-28
Do these help?

[http://kb.mozillazine.org/Problems_printing_web_pages](http://kb.mozillazine.org/Problems_printing_web_pages)
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by mmasroorali on 2009-12-28
> **mörgæs said:**
> Do these help?

[http://kb.mozillazine.org/Problems_printing_web_pages](http://kb.mozillazine.org/Problems_printing_web_pages)

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

This first solution suggests making sure that print spooling is turned on. I checked for this feature in PDF printer (cups-pdf). There was not any option like this. However the cups-pdf.conf does contain a line with Spool. Uncommenting this line did not improve anything.

The second one does not discuss anything about delayed printing.


Know what, Firefox works dazzlingly fast under Vista for the same file.

Thanks for your response.

---

### Post by zacktu on 2010-08-09
I have the same problem.  Printing of an OO Writer document is fast, as is printing with lpr.

---

