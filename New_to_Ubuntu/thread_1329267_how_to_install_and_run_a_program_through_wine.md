---
title: "how to install and run a program through wine"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by greenie2009 on 2009-11-17
I want to use the (free but for windows) pdf xchange viewer, since as far as I can tell from talk on this forum, there is no linux software with the same functions.
I installed wine through synaptics package manager, and downloaded xchange viewer.

What to do now? Where should I extract the .exe file to? How do I run the program through wine?

Thanks a lot, but please keep the answer as simple as possible, I am so new to linux that terminals still scare me ;)

Helene

---

### Post by fromthehill on 2009-11-17
install the program like you do in windows
doubleclick on the exe and hope it works:p
[URL="http://appdb.winehq.org/objectManager.php?sClass=version&iId=11392&iTestingId=42950"]
it should work fine[/URL]
if the installer installs a shortcut in the start-menu it will appear in your ubuntu main menu under wine>programs

you can find the C:/ drive that wine sees under /home/<user>/.wine/drive_c

---

### Post by Jazzy_Jeff on 2009-11-17
Just unzip the program. Open the folder and right click on the .exe file and click on Open with "Wine Windows Program Loader". Follow the prompts.

---

### Post by philinux on 2009-11-17
You might like to take a look at scribus which is in ubuntu's repos.

[http://docs.scribus.net/index.php?lang=en&page=pdfexport1](http://docs.scribus.net/index.php?lang=en&page=pdfexport1)

Install via add/remove or synaptic.

---

### Post by anaconda on 2009-11-17
before trying to run programs with wine you should(have to) type
```
winecfg
```
in terminal. winecfg will create the .wine folder to your home-folder, and use the default settings.

.wine folder contains the virtual C: drive, that windows programs need.

---

### Post by anaconda on 2009-11-17
I tried it.
It installed OK, and seems to work well. (I opened a pdf. file with it.)
I have ubuntu 8.04, and wine vesion 1.0.

---

### Post by greenie2009 on 2009-11-17
> **Jazzy_Jeff said:**
> Just unzip the program. Open the folder and right click on the .exe file and click on Open with "Wine Windows Program Loader". Follow the prompts.
Thanks a lot - that was easy! 
It works now - for other newbies with this issue, I just extracted it to a new folder under my "home" folder, and did as jazy jeff instructed. 

But - does anyone know how to make xchange viewer the standard program when opening pdfs? I ticked this in the installation of xchange viewer, but I still have to right-click on the pdf and choose "open with other application" and "wine windows program loader"
Also, why can't I see xchange viewer in "applications" -> "wine" -> "programs"? (or anywhere else in "applications")

Thanks a lot! you make the leap to linux possible :)
Helene

---

### Post by Jazzy_Jeff on 2009-11-17
> **greenie2009 said:**
> Thanks a lot - that was easy! 
It works now - for other newbies with this issue, I just extracted it to a new folder under my "home" folder, and did as jazy jeff instructed. 

But - does anyone know how to make xchange viewer the standard program when opening pdfs? I ticked this in the installation of xchange viewer, but I still have to right-click on the pdf and choose "open with other application" and "wine windows program loader"
Also, why can't I see xchange viewer in "applications" -> "wine" -> "programs"? (or anywhere else in "applications")

Thanks a lot! you make the leap to linux possible :)
Helene

Just right click on a pdf file and click on properties. Go to the open with tab and see if it lists your program.

---

### Post by anaconda on 2009-11-17
> **greenie2009 said:**
> 
Also, why can't I see xchange viewer in "applications" -> "wine" -> "programs"? (or anywhere else in "applications")

Interesting... The installer did make the required links for me. I have it in 
applications>wine>programs>PDF-XChange PDF Viewer

But You can add the launcher anywhere you want to. Just right-click on the menu, and select "edit menus" and select eg. Graphics and then select the New item from there, and you can make the launcher. Just give it Any name you want, and type:
wine "C:\Program Files\Tracker Software\PDF Viewer\PDFXCview.exe"
on the "command" 
and then select OK.

---

### Post by greenie2009 on 2009-11-17
> **anaconda said:**
> Interesting... The installer did make the required links for me. I have it in 
applications>wine>programs>PDF-XChange PDF Viewer

But You can add the launcher anywhere you want to. Just right-click on the menu, and select "edit menus" and select eg. Graphics and then select the New item from there, and you can make the launcher. Just give it Any name you want, and type:
wine "C:\Program Files\Tracker Software\PDF Viewer\PDFXCview.exe"
on the "command" 
and then select OK.
Thanks a lot anaconda - I got it in applications now - and I'm amazed at how easy it is to customize the menu!!!

---

### Post by greenie2009 on 2009-11-17
> **Jazzy_Jeff said:**
> Just right click on a pdf file and click on properties. Go to the open with tab and see if it lists your program.

Hmm it doesn't list xchange viewer, but when I open with "wine windows program loader" it opens the pdf in xchange viewer. But is it possible to use this as the default pdf viewer? So I don't have to right-click and choose the program every time (if I just double click, it opens in evince)

Thanks
Helene

---

### Post by Jazzy_Jeff on 2009-11-17
> **greenie2009 said:**
> Hmm it doesn't list xchange viewer, but when I open with "wine windows program loader" it opens the pdf in xchange viewer. But is it possible to use this as the default pdf viewer? So I don't have to right-click and choose the program every time (if I just double click, it opens in evince)

Thanks
Helene

When you checked the list did you choose add below the list and see the list of programs? I am not sure if it will be listed or not.

---

### Post by greenie2009 on 2009-11-18
> **Jazzy_Jeff said:**
> When you checked the list did you choose add below the list and see the list of programs? I am not sure if it will be listed or not.

I tried, but it's not in the list (it should be in "bin", right?)

---

