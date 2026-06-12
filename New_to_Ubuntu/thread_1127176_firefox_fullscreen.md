---
title: "firefox fullscreen"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Bearded-flower on 2009-04-16
i have run into a problem of late whenever i start up firefox it starts it in full screen and you cant get to the ubuntu  menu bar 
any ideas?

---

### Post by theozzlives on 2009-04-16
hit f11

---

### Post by Bearded-flower on 2009-04-16
Brilliant, thanks

---

### Post by Bearded-flower on 2009-04-16
how do you change the title of the thread to put [SOLVED] init?

---

### Post by _Purple_ on 2009-04-16
You can click on "Edit Tags" and add a tag "SOLVED" to the thread.

---

### Post by Bearded-flower on 2009-04-16
weres edit tags?

---

### Post by _Purple_ on 2009-04-16
You can see the "Edit Tags" marked with black in the attached image. Click "Edit Tags", type "SOLVED" under "Add Tags" and hit "Save Changes".

---

### Post by binbash on 2009-04-16
Instead of double hit f11, do this to prevent this kind of things in the future : 

go to compizconfig settings manager then workarounds plugin and untick legacy fullscreen support.

---

### Post by superprash2003 on 2009-04-16
this happens even to those who dont use compiz

---

### Post by Bearded-flower on 2009-04-16
Yeah the compiz thing seemed to have worked, i was about to post is there a way without midlesley hitting F11 thanks.

---

### Post by squee on 2009-04-16
I'm still having this problem. Went away for ages but must have come back in the last FF update. Is there a more permanent fix? I dont have the compiz control panel (that I can see in my menus.)

---

### Post by superprash2003 on 2009-04-17
compiz isnt installed by default.. so you wont see the menu..try this [http://www.prash-babu.com/2009/03/how-to-fix-firefox-automatically-opens.html](http://www.prash-babu.com/2009/03/how-to-fix-firefox-automatically-opens.html)

---

### Post by hesjnet on 2009-04-17
What I did to fix this problem is very simple: install opera :D

No really, here is what you do:
[LIST=1][*]Open firefox[*]Hit F11[*]Click the maximize button up in the right corner 2 times[*]restart firefox
[/LIST]

That did it for me.

---

### Post by Big Luke on 2009-04-17
I am no expert but I have run into this problem as well.  I think it is caused by javascript resizing the window.  What I figured out is that the window is UN-maximized and then re sized to be larger than your screen resolution.  So when you maximize it, everything fits.  So what I did is re size my UN-maximized window to my liking and viola.  

The reason I have come to the conclusion that it is due to javascript is, whenever I go to certain websites it will happen.  Im sorry I cannot explain it any better, if you have any questions just ask, id be happy to help.

---

### Post by squee on 2009-04-17
From one of the above links.

into URL bar type about:config   press enter

search for: browser.fullscreen.autohide

If it is set to True, double click to change to false.

restart firefox.


Should work, but I havent fully tested it yet.

---

