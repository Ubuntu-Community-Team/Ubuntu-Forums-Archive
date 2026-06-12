---
title: "How are printer options supposed to work?"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by theplainstyle on 2011-05-02
Hi there,

I have installed an HP Officejet 8000 printer on my Ubuntu 11.04 system.  Printing seems to work great, except for the following issue.

Under 'system settings - printing' selecting printer properties allows me to set different options including colour vs black & white printing, pages per side, resolution, etc. However, when I go the print dialog for an application and select the printer, my 'default options' are not necessarily set.

For example, even though I've selected black only printing under system settings for my printer, the gedit text editor doesn't use that setting and instead selects colour printing by default. Printing from a different application like Firefox seems to work better, but even it doesn't follow the setting for 'pages per side'. Every application seems to work a little differently.

I would assume that the settings in an application's print dialog should honour the system printer settings unless I manually override them.

Is this a bug, a feature or am I just not getting how print dialogs interact with printer system settings?

Ideally, I would like to have a few different printer icons setup under system settings with different default settings so I can quickly set a number of options by only having to select the appropriate 'printer' from an application's print dialog.

Thanks.

---

### Post by Alistair George on 2011-09-19
This is the thing thats annoying in Linux. Yours is a very valid question and its been raised elsewhere in several guises, but there has not been a satisfactory answer to the problem.
If you dont get an answer, it usually means its not fixed.
The same problem has been raised as bug, but nobody has bothered to address it.
Cheers,
Alistair.

---

### Post by abnordude on 2011-09-19
Well......
I don't seem to have that problem.
I use natty.

In my PC, gedit, mozilla and also libreoffice all seem to use the default settings that I had applied.

---

### Post by Alistair George on 2011-09-19
> **abnordude said:**
> Well......
I don't seem to have that problem.
I use natty.

In my PC, gedit, mozilla and also libreoffice all seem to use the default settings that I had applied.
Interesting. 
I am doing a printer review for one of our printers in the office, its a Brother MFC-795CW, and I was blaming the print drivers for not remembering settings by default. Later I used another printer, a HP PSC1210 a good old workhorse. But then I discovered that you can have eg Grayscale set in System/Admin/Printing (Natty) for both printers and they come up with different in pre-print dialog. So you might change them in pre-print dialog and next print they have reverted back to some other setting. Most frustrating; consistent in its inconsistency, and applies to any printer we have here, on various Ubuntus eg Mint/Julia/Katya and Ubuntu
If you Google Ubuntu save print dialog there are many other issues reported.
Cheers,
Alistair

---

