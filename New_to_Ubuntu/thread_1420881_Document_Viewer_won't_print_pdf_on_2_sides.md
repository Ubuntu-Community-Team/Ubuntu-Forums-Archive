---
title: "Document Viewer won't print pdf on 2 sides"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by FredVanH on 2010-03-03
Hi.  My HP Photosmart C6180 prints everything (i.e. OpenOffice.org printouts) on 2 sides on demand;  but not a pdf out of Document Viewer 2.28.1.

I went to print online a bank statement which the bank put up as a *.pdf file.  When I hit Ctrl-P I got the Document Viewer dialog.  When I clicked its Page Setup tab, the only option available under the "Two-sided" selection was "One-sided".

In other apps, such as the OpenOffice.org ones, this dropdown list has a "duplex" option of "long edge - standard" which, when selected, yields printing on both sides of the sheets.

To get to that plateau, I had had to go into System | Administration | Printing, double click the HP C6180 printer icon, click the "Installable options" line, and checkmark "Duplexer Installed".  I went in there again this time to check and those settings were still there.

So, to get the document printed out  on 2 sides, I had to go back to my old Windows machine and do it.  This isn't the way I want to go.  Any ideas for printing a pdf on 2 sides of the sheet with Document Viewer (or any other utility) in Ubuntu?

Thanks,
Fred

---

### Post by LowSky on 2010-03-03
Try Adobe Reader

[http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.3.1/enu/AdbeRdr9.3.1-1_i386linux_enu.deb](http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.3.1/enu/AdbeRdr9.3.1-1_i386linux_enu.deb)

---

### Post by FredVanH on 2010-04-02
Thanks, Low Sky, for your informative answer.  I didn't get time to try it until now;  but when I did it worked perfectly!\\:D/
Regards,
Fred

---

### Post by bebugz on 2010-07-03
I have also tried acroread and it works fine for manual two-sided printing as well.

I'm printing ODD pages in reverse order and complete the whole stuff by rotating this pages and printing EVEN pages in normal order.

Anyway acroread is worth trying.

---

### Post by d91231 on 2012-01-16
I had this same problem. I adjusted my settings to "Duplex NoTumble" using the System Settings - Printing thing, and then I installed xpdf using the Ubuntu Software Cener. I opened the pdf in xpdf, and then printed it, and it printed double sided. 

So, xpdf seems to be able to print double sided (if the System Settings - Printing is set to double sided).

---

### Post by FredVanH on 2012-01-18
Thanks, d91231, for your kind reply.  I have recently dumped the HP C6180 all-in-one because it won't print decently any more and have replaced it with a Canon MX882.  I haven't had a chance to see what the Canon can do in the 2-sided PDF department; but will soon and, if it won't do it, will certainly try your fix as well as the acroread one.

Anyway, just wanted to thank you for caring and for sharing your knowledge.
Regards,
Fred

---

