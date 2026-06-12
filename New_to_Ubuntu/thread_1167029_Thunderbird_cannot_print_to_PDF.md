---
title: "Thunderbird cannot print to PDF"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Johan-Steyn on 2009-05-22
Hi All,

After realizing that one of our major client's windows mail servers automatically rejected incoming emails that have attachments with .eml extentions as file attachments (when forwarding or adding mail messages as attachments), I wanted to print the email (read receipts, etc,) as PDF and attach the .pdf version, as attachment to the email. 

However I was disappointed to realize that Thunderbird does not have Print-to-PDF capabilities and the .ps filetype (print to file) cannot be read by Windoze users.

After wasting two days getting cups-pdf to print correctly, I have discovered a easy "low-tech" workaround that does not involve scripts.

Simply install the printpdf extention in firefox ([https://addons.mozilla.org/en-US/firefox/search?q=printpdf&cat=all](https://addons.mozilla.org/en-US/firefox/search?q=printpdf&cat=all)).

In Thunderbird, instead of printing to file - save the file as _file_.html (replace name "file" with the actual document's file name) in your documents folder. 

Open the _file_.html (using Firefox) and select the *Print to PDF* option.

Save as _file_.pdf in the documents folder.

That's it! Simply attach the  .pdf document and mail.

Cheers!

---

### Post by arch0njw on 2009-07-25
Can you mark this as solved since you have a solution?

Also, I found that in order to print to PDF from Firefox (I assume the same would be true for Thunderbird), I had to first add a CUPS PDF printer.  I found my help in a blog entry from 2006:  [http://embraceubuntu.com/2006/03/23/print-to-pdf-using-cups-pdf/](http://embraceubuntu.com/2006/03/23/print-to-pdf-using-cups-pdf/)

The pertinent parts are...
> 
[cups-pdf]("http://embraceubuntu.com/2006/03/23/print-to-pdf-using-cups-pdf/cip.physik.uni-wuerzburg.de/%7Evrbehr/cups-pdf/") is the package I was looking for apparently. But unfortunately, this takes just a little setting up.
  Install cups-pdf by using:
$sudo apt-get install cups-pdf
 

...
> 
Add a new printer (System->Administration->Printing) selecting the &#8220;Local Printer&#8221; &#8220;PDF Printer&#8221; option. In the next step choose &#8220;Generic Printer&#8221; and then used the &#8220;Postscript Color Printer (Ver 3)&#8221; driver.



I found the output file going to my "~/PDF" directory, not my "~" directory as noted in the blog.

---

