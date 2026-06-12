---
title: "lightscribe not in menu"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-03-29
Hi All,
 Okay, my first question was about installing the lightscribe .deb package, but I found the answer to installing it after saving it first. Now....how do I get it to show up in my menu?

---

### Post by Lisa Y on 2009-03-29
Hello,

You can add it to your menu, 

System> Pref> Main Menu

You can place a check mark there, OR you can Add a new entry.

---

### Post by AndyP79 on 2009-03-29
> **Lisa Y said:**
> Hello,

You can add it to your menu, 

System> Pref> Main Menu

You can place a check mark there, OR you can Add a new entry.



Okay, it is not in the Main Menu, so, I guess I have to put in a new entry. How do I know what the command is? I downloaded 2 .deb packages. one was lightscribe the other was lightscribe applications. Are these the commands as well as the name?

---

### Post by Sarai the Geek on 2009-03-29
> **AndyP79 said:**
> Okay, it is not in the Main Menu, so, I guess I have to put in a new entry. How do I know what the command is? I downloaded 2 .deb packages. one was lightscribe the other was lightscribe applications. Are these the commands as well as the name?

There are instructions about how to setup the SimpleLabeller software here: [http://www.ubuntugeek.com/installing-lightscribe-simple-labeler.html](http://www.ubuntugeek.com/installing-lightscribe-simple-labeler.html)
However I believe those instructions are written for a prior version of Ubuntu, they're not terribly clear. Here's what to do.
1. Right click on the ubuntu logo in your gnome panel and select edit menus
2. In the left side bar that appears, click Accessories
3. Click the New Item button
4.Enter the following things into the dialogue box:
**Name**:  LightScribe (Simple)
**Command**:  /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler
**Comment**:  Simple CD/DVD Labeler
5. Click the little spring icon off to the side and enter this: 
/opt/lightscribeApplications/SimpleLabeler/content/images/LabelWizardIcon.png
 [B]
[/B] Save it and you're done!
Cheers-

---

### Post by AndyP79 on 2009-03-29
> **Sarai the Geek said:**
> There are instructions about how to setup the SimpleLabeller software here: [http://www.ubuntugeek.com/installing-lightscribe-simple-labeler.html](http://www.ubuntugeek.com/installing-lightscribe-simple-labeler.html)
However I believe those instructions are written for a prior version of Ubuntu, they're not terribly clear. Here's what to do.
1. Right click on the ubuntu logo in your gnome panel and select edit menus
2. In the left side bar that appears, click Accessories
3. Click the New Item button
4.Enter the following things into the dialogue box:
**Name**:  LightScribe (Simple)
**Command**:  /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler
**Comment**:  Simple CD/DVD Labeler
5. Click the little spring icon off to the side and enter this: 
/opt/lightscribeApplications/SimpleLabeler/content/images/LabelWizardIcon.png
 [B]
[/B] Save it and you're done!
Cheers-


Cool, this worked, thanks. I went ahead and copy and pasted it into a OO file, as I have been doing for lots of stuff these days so when I reload I can always go back and redo without spending weeks finding it on here. 
Thanks Again

---

### Post by Sarai the Geek on 2009-03-29
> **AndyP79 said:**
> Cool, this worked, thanks. I went ahead and copy and pasted it into a OO file, as I have been doing for lots of stuff these days so when I reload I can always go back and redo without spending weeks finding it on here. 
Thanks Again

Ah yes, I have a similar set of files. It's an excellent way to keep track of obscure commands and such. :)

---

