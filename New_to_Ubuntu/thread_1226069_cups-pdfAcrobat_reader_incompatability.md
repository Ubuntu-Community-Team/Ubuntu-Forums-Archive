---
title: "cups-pdf/Acrobat reader incompatability"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Mjsch on 2009-07-29
I use jaunty, with cups-pdf to produce pdfs... They open fine on linux machines, and even google docs recognizes them, but when I try to open them from my windows (vista SP1) computer (running adobe acrobat 9) they do not open. 

Is there any way to fix this incompatibility? is it a known bug? It doesn't seem right that pdf files would be incompatible with each other, no?

---

### Post by unutbu on 2009-07-29
This may or may not work, but perhaps it's worth a try:

Install the **tofrodos** package.

Run 
```

unix2dos file.pdf
```

Then see if file.pdf can be viewed on the Windows machine.

---

### Post by selinap on 2009-08-24
Maybe you are producing a postscript file but using .pdf extension by mistake.

Could you open the file using Adobe Acrobat on Ubuntu?

---

### Post by m3topaz on 2010-03-04
> **Mjsch said:**
> I use jaunty, with cups-pdf to produce pdfs... They open fine on linux machines, and even google docs recognizes them, but when I try to open them from my windows (vista SP1) computer (running adobe acrobat 9) they do not open. 

Is there any way to fix this incompatibility? is it a known bug? It doesn't seem right that pdf files would be incompatible with each other, no?

I've just had some fun with Thunderbird and creating PDFs...
I needed to output some emails, so I opened these in Thunderbird and selected 'Print' - which lets me take the option "Postscript/default". In the resulting dialogue I can set the file to have a pdf extension, and while the file created opens in Evince in Ubuntu the Windoze recipient can't open it in Acrobat.
So I install cups-pdf from Synaptic and then get the option under print to select CUPS/PDF, without the print to file option. This produces a smaller file which ends up in /home/username/PDF and this resulting file opens in Acrobat.
So it looks like a subtle difference in printing between print to file and print via an installed cups pdf printer.

---

