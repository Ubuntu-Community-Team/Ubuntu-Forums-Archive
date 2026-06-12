---
title: "CUPS-pdf"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by beew on 2010-06-06
I have installed CUPS-pdf on Ubuntu 10.04. My understanding is that it is supposed to be a virtual PDF printer. but somehow it doesn't always output a pdf document.

 It works beautifully with firefox, but for Opera web pages  and OpenOffice documents it always outputs postscript files instead. When runnning the "print" command in openoffice, for example, the only output option is ps, you cannot check pdf because it is not there! 

I know that openoffice can  export directly to pdf and that it is not difficult to convert from ps to pdf, but since CUPS-pdf is advertised as a pdf virtual printer, it should be able to print to directly to pdf without me having to do the ps to pdf conversion. I actually didn't even notice that until I sent an output document to someone else using the  foxit pdf viewer and he said it was all gebbrish. Evince opens pdf and ps files all the same and I wouldn't have even noticed the outputs were not pdf!

I tried playing with the settings (there aren't that many) but so far  have not been able to change its behaviour. I wonder if anyone has  experienced the same problem and found a solution.

Thanks.

---

### Post by shnshn52 on 2010-08-08
I find that this happens only if I choose "Print to file" after selecting the PDF printer.  If I do not tick "Print to file" then the output will be in pdf format and it will be placed in the PDF folder in the user's home directory.  The only setback in this case is that you do not get a chance name the output pdf file.  The name is automatically created for you using the name of the document.  I guess this makes sense in that the CUPS-PDF printer is a virtual printer and when you print to a real printer the system just output the printed copy to the printer without asking you for a name for the output.

---

