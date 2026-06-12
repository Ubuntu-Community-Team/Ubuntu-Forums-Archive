---
title: "can gimp save in pdf?"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by duruttye on 2009-06-09
Hey there!

I edited some pdf files in gimp and I have to say it's a big step for gimp to be able to edit pdfs. The only thing is, I don't know how save the edited pdf in pdf format :(
Isn't that A little odd? Being able to edit it, but there is no option to export it to pdf, or save it as pdf?

Any ideas, or any plugins that can cover this little thing?

thanx!

---

### Post by dnairb on 2009-06-09
You could try cups-pdf (in Synaptic, or **sudo apt-get install cups-pdf** in terminal)

It acts as a printer, and "prints" from any app (IIRC) to a PDF file (in the same was as CutePDF on Windows)

Before using, create a folder in your home directory called PDF, otherwise it won't work.

(hmmm, cups-pdf **requires** this folder to exist, yet doesn't create it nor prompt the user to do so. Odd)

---

### Post by Johan-Steyn on 2009-06-09
Hi duruttye,

You can export to PDF in Gimp.

Select File>Print and the **Print to File** option.

Select PDF and print (export) to PDF.

Hope it helps.

Regards,

JS

---

### Post by duruttye on 2009-06-09
Thank you for the replies!

I know I can print it to pdf, but the problem is I can't figure out how to print it in the actual size, because the A4 format, for example is much taller. What I want to save is square (awmost) but it wants to print it to pdf in a way that it will appear a white edge under the actual thing :). 
any ideas on that?

with this print option - for me, at least - doesn't require that folder, I can place it wherever I want...

---

### Post by duruttye on 2009-06-09
well, I could make some changes in the page setup menu, but there are only inches in the paper size. My pdf file has a 1194x1194 pixel size... :)

---

### Post by duruttye on 2009-06-09
Hey!

I figured out (somehow) that the size is exactly 6 inches, so in page setup I made a new custom size with that size, so now, when I print to file, the page is exactly that size.

problem solved :)

---

### Post by llamabr on 2009-06-09
Well done.  Another solution is to save as jpg or png, and use imagemagik to convert:

convert title.jpg title.pdf

will save the layout.

---

### Post by itaylor on 2010-01-17
duruttye,
Thank you for the solution. I'm trying to make a print-ready cover for a self-published book. Lulu.com has strict size requirements for a PDF, and will not scale your file at all.

I'd been struggling with Imagemagick for hours, where the PNG converted to PDF would like fine but be the wrong size, or would be the right size with poor resolution. I'm sure there's a solution in Imagemagick, but I couldn't find it, and the print to PDF solution from GIMP removes a step anyway.

To repeat in more detail for future readers of this forum, here is the problem and solution: Initially GIMP offers a single page size when you print to file as PDF, with no options to change it in the print menu: 
[LIST=1]
[*] In GIMP, go to File > Page Setup and under paper size, select Manage Custom Sizes.
[*] Define the page size to match your requirements (in my case 13" x 9.25" with no margins) and choose this custom size for your document.
[*] Select Print and Print to File, and on the Image Settings tab of the print menu, set the Width/Height equal to the page dimensions you just defined and go ahead with the printing.
[/LIST]

That's it, worked like a charm.
Thanks again for the tip.

---

### Post by AlexanderDGreat on 2010-03-20
Actually this doesn't work, why? In a PDF file you can highlight the text, copy and paste to OOffice or what have you. On the other hand, the process described on this thread only makes GIMP use the name PDF, but underneath it's still JPEG.

Try highlighting your "saved" PDF texts and see if you can select a text. Hope this clears this one up.

---

### Post by gavinlamont on 2010-06-23
I installed cups-pdf, tried to print something and it automatically created a PDF file in my home folder, where the successful print went.  I've tried going the OpenOffice route, but the files get huge.  

Thanks

---

### Post by AlexanderDGreat on 2010-06-24
I installed cups-pdf - do you really need to install this? Any installation of Ubuntu has already a function print-to-file, which can generate pdf's, not sure why you still need cups-pdf.

---

### Post by nanonils on 2010-10-11
Print as (save as) PDF does not work on my current Maverick installations with GIMP when I print a JPG. It creates only a white page.

---

### Post by allankelly on 2010-10-28
Thanks for this discussion. Print to PDF works for me: ubuntu 10.04, gimp 2.6.8-2ubuntu1.1, cups-pdf is not installed.

I checked the comment regarding "GIMP does not save as PDF, only renames and actually saves JPEG", and it's wrong on my machine. Proof:

```
akelly@ubuntu:~$ strings doc.jpg | head -1
JFIF
akelly@ubuntu:~$ strings doc.pdf | head -1
%PDF-1.4

```
Cheers, al.

---

### Post by galv on 2011-03-21
Creating a custom size paper solved my issue. Thanks! :)

---

### Post by JT42 on 2013-03-20
> **itaylor said:**
> duruttye,
Thank you for the solution. I'm trying to make a print-ready cover for a self-published book...

To repeat in more detail for future readers of this forum, here is the problem and solution: Initially GIMP offers a single page size when you print to file as PDF, with no options to change it in the print menu: 
[LIST=1]
[*] In GIMP, go to File > Page Setup and under paper size, select Manage Custom Sizes. 
[*] Define the page size to match your requirements (in my case 13" x 9.25" with no margins) and choose this custom size for your document. 
[*] Select Print and Print to File, and on the Image Settings tab of the print menu, set the Width/Height equal to the page dimensions you just defined and go ahead with the printing. 
[/LIST]

That's it, worked like a charm.
Thanks again for the tip.

Thank you ancient voices from the past, duruttye and itaylor.  This is the solution I was looking for (also for a book cover.)  It's like [http://xkcd.com/979/](http://xkcd.com/979/) in action! (be sure to read the mouseover text)

---

