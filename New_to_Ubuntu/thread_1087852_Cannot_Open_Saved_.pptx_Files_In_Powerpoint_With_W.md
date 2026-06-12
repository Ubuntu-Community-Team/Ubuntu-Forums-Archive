---
title: "Cannot Open Saved .pptx Files In Powerpoint With Wine"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by swagner on 2009-03-05
I recently installed Microsoft Office 2007 in Wine.  I cannot open previously-saved, on a Windows computer, powerpoint (.pptx) files with Powerpoint.  I CAN open files that have been saved using Powerpoint with Wine.

When I try to open the previously-saved on Windows files, I get the following pop-up message:

"The document 'document_name.pptx' caused a serious error the last time it was opened.  Would you like to continue opening it?"

When I select "Yes", the following message pops up:

"Microsoft Office Powerpoint has encountered a problem and needs to close.  We are sorry for the inconvenience."  Etc ...


I have a presentation to do Wednesday of next week and I would like to use my computer to present it.  Does anyone know how I can get these Windows-saved files to open?

Thank you,
Sasha

---

### Post by kanikilu on 2009-03-05
I'm not sure if this helps, but if all you need to do is display (not edit) that presentation, you could try the free [PowerPoint Viewer 2007](http://www.microsoft.com/downloads/details.aspx?FamilyID=048dc840-14e1-467d-8dca-19d2a8fd7485&DisplayLang=en), which should work under wine, at least according to WineHQ (haven't tried it myself).

---

### Post by linuxuser21 on 2009-03-05
Try changing it from .pptx to .HTML.  Open it with Powerpoint and see if that works.

---

### Post by swagner on 2009-03-05
I tried changing the document to .html and that was unsuccessful.  I received the same error pop-up message as before.

I also tried the Microsoft Office Powerpoint Viewer (which installed with no problem) but I am now receiving a message that says "This file requires the Compatibility Pack for the 2007 Office system to view its contents".


Thank you for your speedy responses!

---

### Post by kanikilu on 2009-03-05
> **swagner said:**
> I am now receiving a message that says "This file requires the Compatibility Pack for the 2007 Office system to view its contents". Are you sure you got the 2007 Viewer and not one of the older ones (e.g. 2003)? I don't see why it would need a compatibility pack :confused:

---

### Post by swagner on 2009-03-05
Yes, I downloaded the 2007 Viewer version, I was confused with that pop-up as well.

---

### Post by ashwinhgtx on 2009-03-05
Doesn't OpenOffice Impress support pptx files? Have you tried using that?

---

### Post by djbushido on 2009-03-05
Openoffice 3.0 and beyond does in fact support reading only of .***x files. What happens is that they are sent to a plugin and converted to standard office files and then read. So you can probably just install openoffice and it should work.

EDIT: To do this, go to this site: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)
NOTE: The repo version of openoffice is 2.4.7, which is why you need to do this

---

### Post by swagner on 2009-03-05
I know that O.O. will open .pptx files (I have tried already), but I have images and whatnot that doesn't translate well to O.O. from Microsoft.

---

### Post by ashwinhgtx on 2009-03-06
> **swagner said:**
> I know that O.O. will open .pptx files (I have tried already), but I have images and whatnot that doesn't translate well to O.O. from Microsoft.

Can't you modify the small errors which you see after opening the pptx in OpenOffice, then save it as a ppt or odp?? I don't think there will be any more problems than some overlapping text and images.

Or you could ask a friend who has Windows and Office 07 to open the pptx and convert it to ppt for you.

---

### Post by swagner on 2009-03-06
kanikilu helped me by converting my .pptx file to a .pdf.  Unless someone has an idea about fixing the underlying Microsoft Office or Wine issue, I think I'm going to convert the presentation to a .pdf file and do it that way.  Thanks for all your help!

Sasha

---

### Post by ubuwin on 2009-07-16
Download WINE 1.1.25 deb , installed it and then RESTART your computer. Do not try to operate the program without restarting.  Always better results after installing software and do a restart

---

### Post by Mornedhel on 2009-07-16
> **ubuwin said:**
> Download WINE 1.1.25 deb , installed it and then RESTART your computer. Do not try to operate the program without restarting.  Always better results after installing software and do a restart

1. This thread is a few months old.

2.a This is not Windows. Even in Windows, most of the time restarts after installing applications were just the lazy way of telling you "well the services are installed and you could start them yourself, but since we can't assume you know how to do that it's better if you just restart the whole thing and they'll start next time". Here services actually start when you install them.

2.b I can guarantee you Wine works without restarting.

3. Use repositories instead of manually installing .deb files. If you need the latest (understandable with Wine), add the Wine repository from their website.

4. Now that ksplice (kinda) works, it's theoretically possible never to shutdown a Linux machine except to physically change hardware. This includes updates of all kinds, including replacing the kernel. Yes, you can replace your kernel *while you're using the system*.

---

