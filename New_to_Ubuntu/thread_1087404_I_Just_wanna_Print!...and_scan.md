---
title: "I Just wanna Print!...and scan"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by SadaBena on 2009-03-05
Re: Epson Stylus CX9400F
Greetings! I am very new to the Ubuntu world as well as to these good ol' forums, and I am finding myself in a predicament.

I'm currently using Intrepid and I cannot get my CX9400f to print proper colours. On the test print, the red is coming up quite orange, and so on.
I tried walking through the steps stated before, but when I went to

(System -> Administration -> Printing), and renamed the printer "Epson Stylus CX9400F - CUPS+Gutenprint(OpenPrinting LSB 3.2) v5.2.1 Simplified)"

I got an error message saying "CUPS Server Error, there was an error during the CUPS operation: 'client-error-bad-request'"
I then attempted to simply change the Colour mode to "CMY colour", but when I tried a test print there was a printing error, so I went through the troubleshooter, the printer's state message was 'Specified ColourSpace not supported'. 
It turns out that the only colour spaces that I can get to work are RBG Colour and CMYK, both of which are off colour.

And to add insult to injury, I can't get Xsane to recognise the scanner portion either, even after installing 'libsane-extras'. (grrrrrrr)
Any thoughts or comments on either problem would be greatly appreciated.

---

### Post by itix on 2009-03-06
Oh... I'm no good at these things!
My canon ip2000 printer and whatever-it's-name-is scanner just works perfectly.

Could you perhaps try to delete your printer and scanner from "printing" and insert them in the computer again. That should probably reconfigure their settings.

---

