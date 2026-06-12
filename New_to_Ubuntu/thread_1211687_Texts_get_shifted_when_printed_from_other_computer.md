---
title: "Texts get shifted when printed from other computers"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by mmasroorali on 2009-07-12
Dear All,
We have a HP LaserJet 4200 printer connected to an Ubuntu machine. This printer is published, so we can also print from other computers. So, we have a machine where the printer is connected to parallel port and there are around twenty other machines which uses this printer over a LAN.

But when printed from other machines (running the same version of Ubuntu and using the same driver), the text gets vertically shifted. The same thing happens when printed from any other machine in the LAN.

I do not have a clue how to debug this problem. Any suggestion will be greatly appreciated.

Regards.

---

### Post by gackt on 2009-07-13
First of all, what do you trying to print? Does it happen to all kind of file? picture and text?

---

### Post by mmasroorali on 2009-07-13
> **gackt said:**
> First of all, what do you trying to print? Does it happen to all kind of file? picture and text?

The answer is yes for all types of file. The most prevalent type we use here printing reports from web pages for a big project. I tried using printing these pages to pdf files, which looked alright is document viewer. When I printed this pdf file in printer, again the top got truncated. The same thing happened in case of open office text documents.

I am simply clueless here. Any suggestion will be appreciated.

---

### Post by gackt on 2009-07-13
So there is no single computer that can print out with right margin nor size? Ok sound like global settings that mess up. Have you try to setup the printer option?

System > Administration > Printing
select your printer > Right click > Properties
Go to printer option in the menu
And try to modify the option there that match your need

Printing directly from web page is usually followed by error regarding the margin, but first of all we have to make sure that printing from pdf or open office is working perfectly first (all printed beautifully). let me know the result from modifying the printer options.

Regards

---

### Post by mmasroorali on 2009-07-14
Actually I have already checked the printer setup option before. The settings over there are exactly the same as I see in cups. 

One thing I notice when I print the test page from system printer setup. The left, right, and bottom side lines match with the edge of the paper, the top side has gone out of paper. Can we call it vertically magnified?

Any suggestion will be appreciated.

---

### Post by gackt on 2009-07-14
Ok try this, lets make the paper setting bigger than the file it self. Say you want to print A4 document, have the printer set to F4 (which is taller as we all know) and see if the top margin printed out correctly or not.

---

### Post by mmasroorali on 2009-07-14
Could you please clarify it a little more? When you say `have the printer set it to F4', what is exactly meant here? Do I set the paper size in physical printer or set the paper size in cups (or system -> printers ..)?

Thanks always.

---

### Post by gackt on 2009-07-14
Sorry there, "F4" in my country referring to size of paper that is slightly more taller than "A4" sized paper. Here what is I'm having in mind: Maybe the truncated text is the result of improper paper size, What if we feed taller paper, will it still truncated or not, this is the thing i want to know. Try to set it in physical printer. I'm sorry i can not help you clearly.

---

### Post by mmasroorali on 2009-07-15
> **gackt said:**
> Sorry there, "F4" in my country referring to size of paper that is slightly more taller than "A4" sized paper. Here what is I'm having in mind: Maybe the truncated text is the result of improper paper size, What if we feed taller paper, will it still truncated or not, this is the thing i want to know. Try to set it in physical printer. I'm sorry i can not help you clearly.

F4 size is not available in this part of the world. May be I will try with legal size which is taller than A4 and almost the same wide.

Last night, I defined a slightly shorter paper (than A4) as custom size in Firefox and applied it in File->Page Setup in the client computers. Now we can print from all of these without the top being truncated. I got this hunch from your suggestion of testing a taller paper. Please accept my sincerest thanks. We will use this until anybody can come up with something more substantial.

---

### Post by gackt on 2009-07-15
Ok Then and sorry for not giving you the proper solution. please keep posting about your finding. Cheers

---

