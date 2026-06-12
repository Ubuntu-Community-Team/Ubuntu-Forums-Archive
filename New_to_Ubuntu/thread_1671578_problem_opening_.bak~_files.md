---
title: "problem opening .bak~ files"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by scottlenn on 2011-01-20
Hello all,

I'm sorry to report I'm having a bit of trouble. I've been writing an article in Abiword 2.8.2 and, as has been happening from time to time, my laptop crashed. Luckily, there seems to be a back-up of what I was working on, saved as a .abw.bak~ file. However, when I open this file, instead of my text, I see what looks like HTML code, ie formatting commands inside triangle brackets. I can see small chunks of my text, but it's a fairly long article and fairly unreadable like this.

Any ideas how to get it back to normal?

Thanks,

scott

---

### Post by ajgreeny on 2011-01-20
What are you opening those .bak files with?  I assume if Abiword made them, Abiword should open them, but you may have them opening in the text editor by default, so try right clicking on one of them and chose open with Abiword.

---

### Post by scottlenn on 2011-01-20
Hi thanks, but I have been opening the file with abiword. Any other thoughts?

---

### Post by scottlenn on 2011-01-20
I'll paste the start of the document as it appears, in the hopes that might help:

                       > [FONT=Courier]<?xml version="1.0" encoding="UTF-8"?>[/FONT]
    [LEFT][FONT=Courier]<!DOCTYPE abiword PUBLIC "-//ABISOURCE//DTD AWML 1.0 Strict//EN" "http://www.abisource.com/awml.dtd">[/FONT][/LEFT]
    [LEFT][FONT=Courier]<abiword template="false" styles="unlocked" xmlns:fo="http://www.w3.org/1999/XSL/Format" xmlns:math="http://www.w3.org/1998/Math/MathML" xid-max="281" xmlns:dc="http://purl.org/dc/elements/1.1/" fileformat="1.1" xmlns:svg="http://www.w3.org/2000/svg" xmlns:awml="http://www.abisource.com/awml.dtd" xmlns="http://www.abisource.com/awml.dtd" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.9.1" xml:space="preserve" props="dom-dir:ltr; document-footnote-restart-section:0; document-endnote-type:numeric; document-endnote-place-enddoc:1; document-endnote-initial:1; lang:en-GB; document-endnote-restart-section:0; document-footnote-restart-page:0; document-footnote-type:numeric; document-footnote-initial:1; document-endnote-place-endsection:0">[/FONT][/LEFT]
    [LEFT][FONT=Courier]<!-- ======================================================================== -->[/FONT][/LEFT]
    [LEFT][FONT=Courier]<!-- This file is an AbiWord document.                                        -->[/FONT][/LEFT]
    [LEFT][FONT=Courier]<!-- AbiWord is a free, Open Source word processor.                           -->[/FONT][/LEFT]
    [LEFT][FONT=Courier]<!-- More information about AbiWord is available at [http://www.abisource.com/](http://www.abisource.com/) -->[/FONT][/LEFT]
    [LEFT][FONT=Courier]<!-- You should not edit this file by hand.                                   -->[/FONT][/LEFT]
    [LEFT][FONT=Courier]<!-- ======================================================================== -->[/FONT][/LEFT]
   
  

Edit: the smiley should read ':x', although it does express approximately how I'm feeling at the moment

---

### Post by ajgreeny on 2011-01-20
Just out of interest, try renaming the file with the **.bak~** at the end removed so it's just **file.abw** again, and see if abiword can then open it normally.

---

### Post by scottlenn on 2011-01-20
Thanks again, but no dice. Removing the '.bak~' and even selecting 'AbiWord File' from the save as menu results in the same thing.

Fully realise this is my own fault for not saving properly, but I think the problem may have resulted from working in another post-crash .abw.bak, saving to that, and after the most recent crash this happened.

---

### Post by scottlenn on 2011-01-20
Thanks again, but deleting the .bak and selecting 'abiword' from the 'save file as type' menu has no effect.

I fully realise I have only myself to blame for this. I seem to think the problem arose when I worked from a previous .bak file, saved to it, and when the laptop crashed again, I opened the file to see the mess before my eyes at this moment. In the past there have been '.abw.bak.bak' files, but not this time... .

---

### Post by ajgreeny on 2011-01-21
Just for my information and peace of mind I have just let Abiword autosave an edited open file, then crashed it on purpose by killing the xsession.

The .abw.bak~ opens by default in gnome on my machine, but it also opens fine with abiword.  I think your file must therefore be corrupt in some way, rather than just a standard abiword backup file.

However when opened in gedit, all the lines of original text from my doc are preceded with:-
<p style="Normal" xid="
followed by an incremental number, so I can get rid of that with gedit "find and replace" which makes finding all the original text a lot easier, and removes a lot of garbage from the text.   You could also use grep in terminal to do a bit of text sorting for you.  It may not help completely, but is perhaps better than nothing.

---

### Post by scottlenn on 2011-01-21
There never does seem to be any way but the hard way. Thanks for your help, regardless.

---

### Post by freak42 on 2011-01-21
> **scottlenn said:**
> Thanks again, but no dice. Removing the '.bak~' and even selecting 'AbiWord File' from the save as menu results in the same thing.

Fully realise this is my own fault for not saving properly, but I think the problem may have resulted from working in another post-crash .abw.bak, saving to that, and after the most recent crash this happened.

I think what the other poster meant is to remove the .back extension with nautilus and then try to open the file with abiword, not saving it with a different name from abiword.

---

### Post by ajgreeny on 2011-01-21
> **freak42 said:**
> I think what the other poster meant is to remove the .back extension with nautilus and then try to open the file with abiword, not saving it with a different name from abiword.
Yes, that's exactly what I meant.  I thought it was pretty clear, but perhaps I shouldn't make assumptions.

---

### Post by scottlenn on 2011-01-21
Sorry, it is absolute beginner talk after all. I've just googled nautilus, but the results don't tell me exactly what you mean. If possible, can either of you explain?

---

### Post by Chronon on 2011-01-21
Nautilus is the default Gnome file browser.

---

### Post by ajgreeny on 2011-01-22
> **Chronon said:**
> Nautilus is the default Gnome file browser.
And if you right click on a file in nautilus you can rename it from the context menu.  What I wanted was for you to rename the .bak~ from **name.abw.bak~** to just **name.abw** and then try opening in abiword.

However, as I said, on my system the **name.abw.bak~** file opens just like a normal abiword file, which is why I suspect your file is corrupt in some way.

---

### Post by scottlenn on 2011-01-24
I tried renaming from Nautilus as well and still no love. Have deleted all the junk within triangle brackets (after trying all the suggestions) and some text is missing, which would seem consistent with the idea that the file is corrupted somehow. Thanks for the help, anyway, and do I mark the thread as 'Solved', despite the lack of a happy ending?

---

### Post by dr.frankinfurter on 2011-10-10
This happened to me too. I was working on my Perl homework and I accidentally yanked the power cord from the wall while getting up to use the bathroom. I opened up the .bak~ file and it's just CSS styling sheet, or whatever. I'm just going to re-do my work in LibreOffice since I know it does a better job of recovering my documents. It's a shame since AbiWord is so light weight and integrates with Gnome really well.

Edit: I really should have tried the renaming thing BEFORE I posted. Got it working now. :p Still kind of clumsy but oh well. :D

---

