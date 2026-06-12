---
title: "LibreOffice Calc"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by arno48 on 2011-06-23
Hello,
Is this the right forum to ask about LibreOffice Calc?
My question is the following
When I open LibreOffice Calc the default  column height is to low and the fonts are to small.
Is it possible to change the default height?

---

### Post by ExileAmongYou on 2011-06-23
Just had a quick look, and the closest thing I could find was the user interface scaling in the options. Hit Tools->Options, go to Libreoffice->View, and bump the scaling up a few percent. Of course, that will probably make your other Office apps bigger as well.

---

### Post by arno48 on 2011-06-23
> **ExileAmongYou said:**
> Just had a quick look, and the closest thing I could find was the user interface scaling in the options. Hit Tools->Options, go to Libreoffice->View, and bump the scaling up a few percent. Of course, that will probably make your other Office apps bigger as well.

Thank you, it is working.
Do you think I just changed the  cell size of the sheet I am working in, or the default cell size?

---

### Post by ExileAmongYou on 2011-06-23
Well I think it changes the default zoom level for all the different LibreOffice apps, i.e. if you open up LibreOffice Writer, the page size/interface will be a bit bigger than it was. I'm not sure how you would do it for just Calc, if the change is bothering you in the other apps.

---

### Post by Elfy on 2011-06-23
You could - open a new spreadsheet - Ctrl+A - use your mouse to set a suitable row height then save it as a _template_.Then use the template organise dialogue to set the new one as default.

[http://wiki.services.openoffice.org/wiki/Documentation/OOo3_User_Guides/Calc_Guide/Setting_a_default_template](http://wiki.services.openoffice.org/wiki/Documentation/OOo3_User_Guides/Calc_Guide/Setting_a_default_template)

---

### Post by dwhite on 2011-06-23
[LIST]
[*]first format a Calc sheet to your liking
[*]now save it:-->  File-Templates-Save
[*]now choose it as the default:
[LIST]
[*]-->  File-Templates-Organize
[LIST]
[*]in template management window select the template you just saved (it will be in the 'my templates' folder)
[*]go to the commands pulldown menu on the right-hand side of the template management window and choose "set as default"
[/LIST]
 
[/LIST]
 
[/LIST]
now the next time you open a calc spreadsheet it will be formatted like you wish

---

### Post by arno48 on 2011-06-23
Thanks, you are quite clear, but when I open the    	 	 	 	 	"commands pulldown menu on the right-hand side of 			the template management window" I have just the following 2 commands:

- Printer set 
- Update

I tried " Update" but the template is not saved

---

### Post by dwhite on 2011-06-23
> **arno48 said:**
> Thanks, you are quite clear, but when I open the                            "commands pulldown menu on the right-hand side of             the template management window" I have just the following 2 commands:

- Printer set 
- Update

I tried " Update" but the template is not saved


you must click on the file you saved as a template to highlight it before using the pulldown menu, here are the steps to do that


[LIST]
[*]first format a Calc sheet to your liking
[*]now save it:-->  File-Templates-Save
[*]now choose it as the default:
[LIST]
[*]-->  File-Templates-Organize
[LIST]
[*]in template management window select the template you just saved (it will be in the 'my templates' folder)  [COLOR=Red]<---to do this [/COLOR]
[LIST]
[*][COLOR=Red]double click the "my templates" folder[/COLOR]
[*][COLOR=Red]now click on the template you saved to highlight it[/COLOR], now
[/LIST]
[*]go to the commands pulldown menu on the right-hand side of the template management window and choose "set as default"
[/LIST]
 
[/LIST]
 
[/LIST]

---

### Post by arno48 on 2011-06-23
> **dwhite said:**
> you must click on the file you saved as a template to highlight it before using the pulldown menu, here are the steps to do that


[LIST]
[*]first format a Calc sheet to your liking
[*]now save it:-->  File-Templates-Save
[*]now choose it as the default:
[LIST]
[*]-->  File-Templates-Organize
[LIST]
[*]in template management window select the template you just saved (it will be in the 'my templates' folder)  [COLOR=Red]<---to do this [/COLOR]
[LIST]
[*][COLOR=Red]double click the "my templates" folder[/COLOR]
[*][COLOR=Red]now click on the template you saved to highlight it[/COLOR], now
[/LIST]
 
[*]go to the commands pulldown menu on the right-hand side of the template management window and choose "set as default"
[/LIST]
 
[/LIST]
 
[/LIST]

Perfect, the mistake was to open a new sheet after  "Save".
Thanks for your clever assistance, now I can match this thread as SOLVED

---

