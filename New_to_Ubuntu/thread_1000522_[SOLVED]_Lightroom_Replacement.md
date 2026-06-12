---
title: "[SOLVED] Lightroom Replacement"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Flirtilizer on 2008-12-03
What are my best choices for replacing lightroom.  I've installed KP Photo, not sure I like it.  No editor built in?  All in one sure would be nice.  I'm not sure it imported my meta data but perhaps I need to look at more than one picture. :)

What do you like?  Why you like it would be nice too. :)

Thanks for the help

---

### Post by Dj Melik on 2008-12-03
You can use Google Picasa, I personally use it and its pretty good.

You can either just download the .deb package: [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)

Or..

1) Go to System > Administration > Software Sources and scroll to the third party software tab.
2) Add the following:

[b]deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free[/b]

3) Open terminal and run sudo apt-get update.
4) Then run sudo apt-get install picasa.

---

### Post by Flirtilizer on 2008-12-03
I have used Picasa, in fact, I bought it when it was a comercial product.  Google bought the compay and made it free.  LOL

Thanks for the instructions, I looked for it in the add on manager but didn't find it.  Perhaps, your instructions will help.  :)

I don't recall it keeping the meta and exitif data in tact.  Hopefully that will change.

I abandoned Picasa when I got my hands on lightroom.  I may stick with t on a windows machine.  I probably will, its not up to Lightroom but it is nice free software, very nice.

---

### Post by anewguy on 2008-12-03
You've probably already heard mention of, and may have already tried it, but GIMP is actually really powerful once you find your way through it menus, add-ons, etc.  I've used it for photo editing, creating animated GIF's, etc..  It does way more than Picassa, but it also has a learning curve not associated with the other easier to use, less powerful but good general managers/editors.  When I first tried it, I hated it.  Now, I just look for more info online when I can't figure something out.  It really is very good.

There are also other free vector editing tools also.  I can't for the life of me remember the name right now, but I did use one for a while that was excellent - sometimes I used it for things that were easier to do in it prior to opening the image in GIMP.

Dave ;)

---

### Post by Flirtilizer on 2008-12-03
Gimp is an editor that I plan to use.  It isn't a photo manager that I have seen so far.  Exitif and meta data are crucial to me.

---

### Post by anewguy on 2008-12-03
Have your tried installing Wine and trying LightRoom in it?  It's possible it may run in Wine and that would still keep you in Linux if you want.  Also, for my own testing on this, is that a free download or is LightRoom a product you must purchase (if a free download I could it in Wine to see if I can get it working)?

Dave ;)

---

### Post by anewguy on 2008-12-03
I downloaded the trial version and tried it in Wine - no go, known problem.

I did find another piece of software (it's not free though) called
LightZone that may be what you are looking for.  It's not cheap, but I found it referenced on the web as a non-free Linux replacement for Lightroom.  They do have a 30-day trial version you can download and try out.

Hope that helps!

dave ;)

---

### Post by Flirtilizer on 2008-12-03
> **anewguy said:**
> I downloaded the trial version and tried it in Wine - no go, known problem.

I did find another piece of software (it's not free though) called
LightZone that may be what you are looking for.  It's not cheap, but I found it referenced on the web as a non-free Linux replacement for Lightroom.  They do have a 30-day trial version you can download and try out.

Hope that helps!

dave ;)

Wow thanks for all the effort..  i tried lightroom in both crossover and wine..  Crossover claims some have got it to work.

I have downloaded that and will take a look at it.  I found another one that looks real good too called Raw Therapee  [http://www.rawtherapee.com/](http://www.rawtherapee.com/)

I don't know how to install either of them.  I'm really a newbie...

I extracted them, now what.  I feel kind of stupid, been playing with computers for over 20 years and all of a sudden I'm back at square one. LOL  Can you help me with this as well?

I'm starting with raw therappee cause it is free.

---

### Post by anewguy on 2008-12-03
I know I used rawtherapy at one time, but I honestly just don't remember how it was at this time, sorry!  I wish you the best in finding what you want.  To install things like lightzone, you do the extract with package manager (normally just clicking on them opens them in package manager) and unpack them to some folder. To execute them you normally would go to the folder you unpacked them to and look for a Linux executable and double-click it.  In the case of lightzone, it wants (on my PC at least) to open a terminal window and then start the GUI.  You can always right-click on these, click on create link, then move the link created to your desktop (pretty much the same as creating a shortcut in Windows).

Let us know how things go and if you need more help.

Sorry I couldn't have been of more help to you!

Dave ;)

---

### Post by C. Wizard on 2008-12-03
digiKam and its companion viewer showFoto.

Personally I like to view images with Gwenview and when an editor is needed I can export the image directly into The Gimp with a mouse click or two. Great combination.

---

### Post by Flirtilizer on 2008-12-04
> **anewguy said:**
> I know I used rawtherapy at one time, but I honestly just don't remember how it was at this time, sorry!  I wish you the best in finding what you want.  To install things like lightzone, you do the extract with package manager (normally just clicking on them opens them in package manager) and unpack them to some folder. To execute them you normally would go to the folder you unpacked them to and look for a Linux executable and double-click it.  In the case of lightzone, it wants (on my PC at least) to open a terminal window and then start the GUI.  You can always right-click on these, click on create link, then move the link created to your desktop (pretty much the same as creating a shortcut in Windows).

Let us know how things go and if you need more help.

Sorry I couldn't have been of more help to you!

Dave ;)

They didn't open in package manager, I don't think.  I'll double check but what is a Linux executable?   )  All I see are .so files.  I even took the extreme measure of opening the manual. LOL  I didn't find anything there.  Raw has online forum but it thinks I'm typing the Capcha wrong.  I often do but wasn't this time.

I'm going to start a new thread on how to install programs.  I thought it was opening in some sort of archive manager.  

Thanks again, you're a big help.

---

### Post by meho_r on 2008-12-04
When extracted the archive, you should see at least two files: rt and rtstart. Double click on rt and that's it.

---

### Post by litago on 2009-02-16
Know that this is solved, but have you tried RawStudio?

---

### Post by Orion8 on 2009-02-16
This is marked "solved" but I would suggest if you don't mind paying for software check out Bibble. It is not so much of a photo manager at this stage (though the much anticipated Bibble 5 release is supposed to add some of that functionality) so much as a RAW photo processor, but it does a GREAT job.  I miss some of Lightroom's function, but have to say that that Bibble does more better (in my opinion) than any of the free options (many of which I have checked out).  I mean, some of the others work okay, but if you need to get though a lot of pictures quickly and do a good job Bibble is the way to go.

---

