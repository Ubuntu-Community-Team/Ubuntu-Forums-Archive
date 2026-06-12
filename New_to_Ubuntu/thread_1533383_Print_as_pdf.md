---
title: "Print as pdf"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-17
i have the option under Printers, but when i try to print from opera or firefox, nothing happens. any suggestions.

---

### Post by odttopdf on 2010-07-17
Can you provide a screenshot if possible?
I think I can help you out if you can provide a screenshot.

Generally speaking, have you configured the PDF Printer to be your default printer for printing so whenever you print something out of Firefox etc it would automatically be printed through your PDF Printer?

Just a thought, I hope it helps...

---

### Post by TimEnid on 2010-07-17
> **odttopdf said:**
> Can you provide a screenshot if possible?
I think I can help you out if you can provide a screenshot.

Generally speaking, have you configured the PDF Printer to be your default printer for printing so whenever you print something out of Firefox etc it would automatically be printed through your PDF Printer?

Just a thought, I hope it helps...

it is set as the default printer, as i dont have a regular printer connected. what would you like a screen shot of?

---

### Post by odttopdf on 2010-07-17
> **TimEnid said:**
> it is set as the default printer, as i dont have a regular printer connected. what would you like a screen shot of?

If you can then please provide a screenshot of what happens after you click on the "Print" from FireFox. Is it possible??

---

### Post by gandaran on 2010-07-18
did you rename the pdf? or just used the default .pdf? if it was the default then check the hidden home files, it will be there.

---

### Post by TimEnid on 2010-07-18
> **gandaran said:**
> did you rename the pdf? or just used the default .pdf? if it was the default then check the hidden home files, it will be there.

found them. but how do i select where i want them saved? and when i click Print to pdf, im not even prompted to name the docs.

---

### Post by Loda on 2010-07-19
Hi, make sure if the pdf is restricted by owner password which prevents 

you from copying, editing and printing pdf files. If so, use a pdf password 

remover to [remove pdf password]("http://www.anypdftools.com/pdf-password-remover.html").

---

### Post by crjackson on 2010-07-19
> **TimEnid said:**
> found them. but how do i select where i want them saved? and when i click Print to pdf, im not even prompted to name the docs.

+1 a VERY common user error.

---

### Post by beew on 2010-07-19
Choose "print to file" instead "PDF", then you can choose the file name and the folder where the output is saved to.

Strange thing though, when I print from firefox the output is pdf as advertised, but when I print from opera the output is actually in postscript (.ps) even though in the print screen I explicitly choose the output format to be pdf rather than ps! 

You wouldn't even notice if you try to open it with Evince (or other document viewrs from the repo) because it opens both pdf and ps files. However, use a different pdf viewer not from the Ubuntu repo such as Foxit or Adobe you would get an error message.

I wonder if others have had the same problem.

I set up cups pdf as my pdf printer.

---

### Post by TimEnid on 2010-07-19
> **beew said:**
> Choose "print to file" instead "PDF", then you can choose the file name and the folder where the output is saved to.

Strange thing though, when I print from firefox the output is pdf as advertised, but when I print from opera the output is actually in postscript (.ps) even though in the print screen I explicitly choose the output format to be pdf rather than ps! 

You wouldn't even notice if you try to open it with Evince (or other document viewrs from the repo) because it opens both pdf and ps files. However, use a different pdf viewer not from the Ubuntu repo such as Foxit or Adobe you would get an error message.

I wonder if others have had the same problem.

I set up cups pdf as my pdf printer.

thanks, this worked.

---

### Post by Webad13 on 2011-01-26
> **beew said:**
> Choose "print to file" instead "PDF", then you can choose the file name and the folder where the output is saved to.

Strange thing though, when I print from firefox the output is pdf as advertised, but when I print from opera the output is actually in postscript (.ps) even though in the print screen I explicitly choose the output format to be pdf rather than ps! 

You wouldn't even notice if you try to open it with Evince (or other document viewrs from the repo) because it opens both pdf and ps files. However, use a different pdf viewer not from the Ubuntu repo such as Foxit or Adobe you would get an error message.

I wonder if others have had the same problem.

I set up cups pdf as my pdf printer.

Same thing happens to me (using Linux Mint Debian), so I think it has something to do with the way in which Opera handles printing - maybe a wrong command is sent to evince.

Have you managed to resolve it? - what happens when you set up cups pdf, are pages in Opera printed in pdf then instead of ps? (I disabled cups since I have no printers attached)

---

