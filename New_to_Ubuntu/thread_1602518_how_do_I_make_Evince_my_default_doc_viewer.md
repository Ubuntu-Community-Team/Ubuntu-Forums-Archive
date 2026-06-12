---
title: "how do I make Evince my default doc viewer?"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by bailey07 on 2010-10-21
I am/was looking for a multi-page tiff viewer and, from the forums, came across Evince.  I am using 9.1.  How do I make Evince my default doc viewer or at the very least get it to come up as an option when I click on the tiff file I want to view.  Thanks.

---

### Post by P4man on 2010-10-21
right click a TIFF, open with, other application. Select "document viewer' (that is evince, verify in custom command a bit lower to see if it fills out evince) and make sure the checkbox at the bottom is selected.

---

### Post by bailey07 on 2010-10-21
Thanks for the quick response P4man

When I right click on the link I have only the options:

open Link in new window
open link in new tab
____________________

bookmark this link
save link as
send link
copy link location

---

### Post by P4man on 2010-10-21
Oh, the file you want to see is actually a hyperlink in firefox  ? And you want firefox to open evince?

Thats going to be a bit harder and may  depend on that website, and how it has defined its MIME types. Is it a link you can post here?

---

### Post by bailey07 on 2010-10-21
not sure - I'll try...  this is an example of the kind of site/link I will be needing to open in the future and it would be great if I could see all pages of the doc - thanks...

[http://public1.co.galveston.tx.us/CaseDocuments.aspx?CaseID=320320&CaseCategoryKeys=PR&NodeID=100,110,120,130,140](http://public1.co.galveston.tx.us/CaseDocuments.aspx?CaseID=320320&CaseCategoryKeys=PR&NodeID=100,110,120,130,140)

When I left click on one of the documents from this page I get only the first page, etc...

---

### Post by P4man on 2010-10-21
OKay, that sort of worked, not really, but I got to a page on that site where I can download those TIFFs,.

You are using  an older version of ubuntu, and therefore firefox as me, so it may be a bit difference, but try this: Click one of those links to a TIFF. A window will popup asking what to do, and suggesting Image Viewer. click on the drop down and select "other". You should get a filebrowser.

In the left pane click "filesystem" then browse to /usr/bin (this could take a while). Find "evince" in that list, and click it, click open. Make sure you select "do this automatically for files..." at the bottom of the previous/next dialogue.

That should be all.

---

### Post by bailey07 on 2010-10-21
I will try..  wait can you tell me how to undo the "automatically do this" I checked last time so I get that window again?

---

### Post by P4man on 2010-10-21
edit > preferences > applications
Select the TIFF content type, and set action to "always ask"

---

### Post by beew on 2010-10-21
I think you may be able to edit mozplugger to do that. 

Download and install mozplugger from Synaptic. Open it by the command ```
gksudo gedit /etc/mozpluggerrc
```If you scroll down you should see a section on documents and a block of  text on tiff. You will see a few commands I think those decide the order  of action firefox (or any browser you install in Ubuntu as Mozplugger  is the universal web pluggin) would take when encounters a tiff file. I  have edited mozplugger to view pdf (postscript) files inline simply by going to the block for pdf (postcript) and move the line with evince to the top of the block(instead of  xpdf)

 You may want to try something like that on the tiff block. I tried copy  and paste the evince line in the pdf block and put it on top in the  tiff block but it didn't work. The lines in the ttf block, however, do  give you a hint of what applications you may need to install to do  inline viewing. If you install the app than I think you just need to  move the corresponding line to the top of the tiff block.

---

