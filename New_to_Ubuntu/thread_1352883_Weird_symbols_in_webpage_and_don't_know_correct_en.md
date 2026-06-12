---
title: "Weird symbols in webpage and don't know correct encoding"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by hanzj on 2009-12-12
Hello,
Am reading a New York Magazine article ([here]("http://www.printthis.clickability.com/pt/cpt?action=cpt&title=The+Abortion+Distortion&expire=&urlID=415703017&fb=Y&url=http%3A%2F%2Fnymag.com%2Fnews%2Ffeatures%2F62379%2F&partnerID=73272")). It looks like the attached screenshot. I've tried changing different encodings. They all still look bad. I looked at the page source but search for "encoding" turned up nothing.

How does one solve such a problem?

Thanks.


UPDATE: The non-print-friendly version of the article ([here]("http://nymag.com/news/features/62379/")) actually looks good. Weird. But I still would like to solve the printer-format webpage.

UPDATE 2: Looks bad in Chromium browser, too.

---

### Post by Some Penguin on 2009-12-12
They're almost certainly quotation marks.  Microsoft's version, specifically.

See l[URL="http://www.dwheeler.com/essays/quotes-in-html.html"]http://www.dwheeler.com/essays/quotes-in-html.html
[/URL]

---

### Post by hanzj on 2009-12-12
Yes, it does appear that they are quotation marks. What's the solution for the web surfer?

---

### Post by Some Penguin on 2009-12-12
Create your own copy of the page.  You can try setting the character set to Windows 1252 as that page suggested, or you can search/replace the offending characters to ordinary quotes -- characters 145-148 need to be changed.

Or access it using IE or the like.

---

### Post by hanzj on 2009-12-12
I changed Encoding to Windows 1252, but the text still looks weird.

Looks okay in Internet Explorer (thank you IEs4Linux!), but wish I didn't have to run IE.

---

