---
title: "Change the background color of pdf files in evince document reader"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2009-04-16
hello...

i need to change the background color of PDF files in evince as a white background is very irritating and tiring to read...

so please please can u make some solution to change the background color ...
or can u provide an alternate solution so view PDF files with a facility to change background color..

thanks ..
shreyansh jain

---

### Post by shreyanshjain8 on 2009-04-16
why i am always neglected in this forum... no one answers my question..

why it is soo can any1 tell me.... :(:(  

i am tired of asking question on this forum .... no one replies me...

---

### Post by shreyanshjain8 on 2009-04-16
why i am always neglected in this forum... no one answers my question..

why it is soo can anyone tell me.... it really discourages the new users... :(  :(



i am tired of asking question on this forum ....but no one replies me...

---

### Post by Hendronicus on 2009-04-16
What is your question?

---

### Post by Ravernomina on 2009-04-16
whats your question... some times people will not answer when your not descriptive or it shard to understand :(

---

### Post by Narvinye on 2009-04-16
Hi! I guess the tile of you post can go a long way.  Is there something specifically that you are having an issue with?  So far so good on getting people to respond right?  I'd say it's like working with any computer system... don't give up.

---

### Post by tegnoto89 on 2009-04-16
Just a tip: don't bump your threads unless it's been a few days.  There are people who go around specifically looking for threads with zero replies so they can try and help out.

---

### Post by shreyanshjain8 on 2009-04-16
thanks sir for replying this time .. my question i posted in the threads below....

anyways i am posting it here also...

i need to change the background color of PDF files in evince as a white background is very irritating and tiring to read...

so please please can u make some solution to change the background color ...
or can u provide an alternate solution so view PDF files with a facility to change background color..

thanks ..
shreyansh jain

---

### Post by Sef on 2009-04-16
1) You can bump your question up if there have been no activity on it for 24 hours.  To bump a thread, click reply and type in bump.  (If a thread is bumped sooner than 24 hours, then a warning or infraction may be given.)

2) The person knowing the answer may not be on now.  They could be on in 5 minutes, 5 hours, 5 days or later.

3) Your problem may be not a common one, so only a few the answer.  

4) Patience is required.  Sometimes threads are answered quick; sometimes slow.

5) If more than 24 hours have passed, then go bump your thread and possibly someone can help you out.

---

### Post by Sup3r3g0 on 2009-04-16
Personally, I've never tried it before, but I *think* you can download PDFedit and use that to change the background color of a PDF.

Hope this helps

---

### Post by Hendronicus on 2009-04-16
This is for shreyanshjain8's question. I cannot find a way to configure Evince to change the background color of a PDF. However, another fine program, KPDF, has this feature. You may want to try KPDF.

---

### Post by shreyanshjain8 on 2009-04-16
hey thanx for replying dear..

i had this PDFedit .. and i tried to change from it.. but there is no option to change the background... although font color can be changed..but i want to change the background...

anymore help...!!!

---

### Post by Hendronicus on 2009-04-16
I cannot find a way to configure Evince to change the background color of a PDF. However, another fine program, KPDF, has this feature. You may want to try KPDF.

---

### Post by shreyanshjain8 on 2009-04-16
hey thanx alot dear...

it worked...!!!!

---

### Post by Hendronicus on 2009-04-16
The only downside I could see is that some people don't like mixing the looks of Qt and GTK+ together. I don't mind it so much, but I still try to keep separate GNOME and KDE desktops.

---

### Post by shreyanshjain8 on 2009-04-16
but is there anything wrong in mixing GTK+ and QT ,......

what you say about this...???

---

### Post by kpkeerthi on 2009-04-16
You can us qgtkstyle to make your Qt (KDE) apps look GNOME-like in GNOME.

[http://labs.trolltech.com/page/Projects/Styles/GtkStyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle)

---

### Post by Hendronicus on 2009-04-16
No, shreyanshjain8, there is nothing wrong with mixing them.  kpkeerthi, I'll look into that, I'm really into giving my desktops their own look and feel.

---

### Post by gandaran on 2009-04-16
evince is a pdf reader, if the pdf has a white background it'll show a white background, you cant change it with evince, but you can edit all your pdf's with a pdf editor (pdfedit, xournal and pdf extension for open office) to make changes.

---

### Post by meditatingfrog on 2010-08-29
I kind of know what the user is looking for, which is for evince to allow for different colors when reading, but not to actually alter the file.  The problem is I don't really think pdf's were really designed to be used for reading, it is more a format of what the file will look like printed.  And, of course, we don't want to print the file out with black background and light text.

What I've actually been doing is copying the entire contents of pdf books that I want to read, and pasting it into a text file, then reading it in gvim.  Unfortunately, for most files this doesn't really work, probably has something to do with how the text is encoded.  

If I were a developer, I would probably try downloading the evince source code, to see if I could add this feature easily.  But, it probably isn't easy to add such a feature, and would be nigh impossible for such an uninformed coding loser as myself.

---

### Post by TeoBigusGeekus on 2010-08-29
Ctrl+i will invert the colors of the document.

---

### Post by meditatingfrog on 2010-08-29
> **TeoBigusGeekus said:**
> Ctrl+i will invert the colors of the document.

I tried ctrl+i but it didn't work.  What version of evince are you running?  I have 2.26.1.

---

### Post by uRock on 2010-08-29
Do you have effects enabled in System> Preferences> Appearance (Visual Effects tab)

---

### Post by meditatingfrog on 2010-08-30
> **uRock said:**
> Do you have effects enabled in System> Preferences> Appearance (Visual Effects tab)

yeah, i had them set to normal.  i even set them to extra, but ctrl+i still doesn't invert the colors in evince.

---

### Post by TeoBigusGeekus on 2010-08-30
> **meditatingfrog said:**
> i tried ctrl+i but it didn't work.  What version of evince are you running?  I have 2.26.1.
2.30.3.2

---

### Post by uRock on 2010-08-30
> **meditatingfrog said:**
> yeah, i had them set to normal.  i even set them to extra, but ctrl+i still doesn't invert the colors in evince.
I just realized that the syntax is wrong. It is Super+N to invert the colors

---

### Post by meditatingfrog on 2010-08-30
> **uRock said:**
> I just realized that the syntax is wrong. It is Super+N to invert the colors

Super + N worked (after I went into keyboard prefs -> layouts -> layout options -> compose key composition and unchecked "left win").

Thanks, very cool.

---

