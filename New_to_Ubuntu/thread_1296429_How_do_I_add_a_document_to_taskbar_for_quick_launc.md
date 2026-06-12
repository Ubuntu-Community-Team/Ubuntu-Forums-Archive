---
title: "How do I add a document to taskbar for quick launch"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by bexpert on 2009-10-20
How do I add a document to the panel so that I can launch it quickly? 

I want to add an OpenOffice Impress file that I use often. When I drag it down there, I get an utterly mysterious dialog box that wants me to create a "launcher" or something. 

I would like to be able to click on the file and have it open in Impress. If you could help me do it GUI-wise, I'd be in your debt.

Thanks.

---

### Post by Cuddles McKitten on 2009-10-20
> **bexpert said:**
> How do I add a document to the panel so that I can launch it quickly? 

I want to add an OpenOffice Impress file that I use often. When I drag it down there, I get an utterly mysterious dialog box that wants me to create a "launcher" or something. 

I would like to be able to click on the file and have it open in Impress. If you could help me do it GUI-wise, I'd be in your debt.

Thanks.

You were on the right track!  Drag and drop that file onto a panel.  Then, when the launcher menu pops up stick this in before the filename in the "command" box: "ooffice -impress " without the quotes.  That tells GNOME to open it as an Impress file.  Once you're done, just press close and the button should work.

**Short version**: change the "command" box in the properties of the launcher to "ooffice -impress FULL_FILENAME_GOES_HERE" without the quotes.

---

