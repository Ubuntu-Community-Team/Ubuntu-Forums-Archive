---
title: "where is/how to add Evince document viewer?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by shneader on 2009-07-28
i tried searching the forums for this, but didn't get anywhere. this is going to seem like a stupid question, but....

where is the icon to launch Evince Document Viewer to view my PDF files? It is already installed, and it is my default program to view PDF's, but I cannot see an icon for it in my Applications > Accessories or Applications > Office. Where is the icon to launch it? Also, I want to add a shortcut to it on my panel, but I can't find the icon to drag there.

Thx.

---

### Post by lisati on 2009-07-28
double-clicking on the file you wish to view should do the trick.

---

### Post by shneader on 2009-07-28
> **lisati said:**
> double-clicking on the file you wish to view should do the trick.

yes, thank you, I know that's how to open a .pdf file. but, I want to open the eVince PROGRAM alone. where is the icon for the program? thanks.

---

### Post by Chronon on 2009-07-28
Yeah, I don't know either.  I launch it from bash or by clicking on a supported file type in the file browser.

---

### Post by jmszr on 2009-07-28
shneader,

You will find it under Applications > Graphics. It is the stylized "e" followed by Document Viewer. Drag-and- Drop the icon.

---

### Post by tea for one on 2009-07-28
> **shneader said:**
> yes, thank you, I know that's how to open a .pdf file. but, I want to open the eVince PROGRAM alone. where is the icon for the program? thanks.

Assuming that you are using Ubuntu, I found Evince via Applications > Graphics > Document Viewer.

---

### Post by shneader on 2009-07-28
> **tea for one said:**
> Assuming that you are using Ubuntu, I found Evince via Applications > Graphics > Document Viewer.

Yes, I am using Ubuntu. I have looked there, but it is not there. That why I am so confused. So, how can I re-add the icon back to Applications > Graphics > Document Viewer?

---

### Post by kostkon on 2009-07-28
Its menu item is hidden. You need to right-click on your menu and select *Edit Menus*. Then you need to go in *Applications &#8594; Graphics* to enable it. Just click on its checkbox and that should be it.

---

### Post by RomeReactor on 2009-07-28
> **shneader said:**
> Yes, I am using Ubuntu. I have looked there, but it is not there. That why I am so confused. So, how can I re-add the icon back to Applications > Graphics > Document Viewer?

Hi. It should be there, only the icon doesn't show by default because there's really no need to open Evince alone. Right-click on the Ubuntu menu in the top panel, select "Edit menus" and go to "Applications->Graphics"; check the box next to "Document Viewer" and you should now see it in the menus.

---

### Post by jmszr on 2009-07-28
shneader,

Edit: Already answered.

---

### Post by nhasian on 2009-07-28
you could also just launch it from a terminal with

```
evince
```

---

### Post by shneader on 2009-07-28
got it. thx! i'll have to remember this.

---

### Post by kryos on 2009-07-28
> **shneader said:**
> i tried searching the forums for this, but didn't get anywhere. this is going to seem like a stupid question, but....

where is the icon to launch Evince Document Viewer to view my PDF files? It is already installed, and it is my default program to view PDF's, but I cannot see an icon for it in my Applications > Accessories or Applications > Office. Where is the icon to launch it? Also, I want to add a shortcut to it on my panel, but I can't find the icon to drag there.

Thx.

I could not find it in the menus either.  Had to create a menu entry pointing to its location in /usr/bin.  Easy to add to menus using "Main Menu" in Gnome Control Center.  Will need to install the control center through Synaptic/? first.

Good luck

---

### Post by kryos on 2009-07-28
Just a note:  KostKon and RomeReactor - I can see maybe why some confusion.  My installation of Hardy has Applications/Other/Menu Editor which is different from the one presented using your method.  There is no Evince selection or any way to add to the menu selections.  Very strange!

---

### Post by all_mighty_dollar on 2012-12-29
Thanks.

---

### Post by cariboo on 2012-12-29
This is a 3 year old thread, next time you, all_mighty_dollar, read an older thread, just read it and move on, no need to thank any one. Thread closed.

---

