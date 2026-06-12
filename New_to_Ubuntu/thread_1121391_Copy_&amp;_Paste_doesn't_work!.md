---
title: "Copy &amp; Paste doesn't work!"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by hiloguy on 2009-04-10
Ubuntu 8.10: I can't copy-paste from one app to another.  Like from Firefox to Evolution, OO to Evolution or back, whatever. It doesn't work.

Is this a common problem?  Is there a fix?  It really is a pain!

Thank you!

---

### Post by Didius Falco on 2009-04-10
[LEFT]What method are you trying to use? What are you trying to copy-paste? I have no problem selecting what I want to copy, right clicking and select copy, then putting the cursor where I want to paste and right-clicking and selecting paste.

Try out 

ctrl-insert to copy

Shift-insert to paste

if the first method is giving you problems.
[/LEFT]

---

### Post by fabricator4 on 2009-04-10
Is this with the hotkeys?  Have you tried doing it through the Edit dropdown?

In a terminal the hotkeys are different - <shift><ctrl>C for copy instead of <ctrl>C

Chris

---

### Post by Alex82 on 2009-04-10
hello,
I use the edit drop down but it will only paste if i keep both applications open. ( i.e the one I am copying from has to be open for the paste dropdown to work.)

---

### Post by fabricator4 on 2009-04-10
> **Alex82 said:**
> hello,
I use the edit drop down but it will only paste if i keep both applications open. ( i.e the one I am copying from has to be open for the paste dropdown to work.)

That's very odd behaviour.  Try the <ctrl><insert> and <shift><insert> method.  Does it work the same way?

Also try right-click as suggested.


There's no reason why you'd need to have the other application open when you do a paste.

Chris

---

### Post by hiloguy on 2009-04-10
I've been using control-c and control-v, also tried the copy-paste icons and neither method works. I'll try the right-click trick tomorrow when I'm back on the one of the Linux boxes. 
 OOPS.  Yeah, we still have an XP machine in the office and will have until we get all the rest of the minor glitches taken care of in the Ubuntu boxes.  They are both running 8.10 now which works great on almost everything.

---

### Post by 3rdalbum on 2009-04-10
It's normal for you to need both programs open when you do a copy-and-paste. It's a limitation of Xorg. (anyone who develops Xorg and disagrees, please flame away).

You can get around this limitation by installing "glipper" or some other clipboard manager, and setting it to run on login; then as long as glipper is open you can still paste as normal.

---

### Post by Alex82 on 2009-04-10
> **fabricator4 said:**
> That's very odd behaviour.  Try the <ctrl><insert> and <shift><insert> method.  Does it work the same way?

Also try right-click as suggested.


There's no reason why you'd need to have the other application open when you do a paste.

Chris

nope if the document is closed it wont paste? it is strange but no big drama, i have caught myself out a few times though!

---

### Post by fabricator4 on 2009-04-10
> **Alex82 said:**
> nope if the document is closed it wont paste? it is strange but no big drama, i have caught myself out a few times though!

Oh! That's odd.  Googling it finds a (kind of) fix here:
<code>
[http://www.feedelite.com/92/how-to-fix-the-ubuntu-clipboard-problem](http://www.feedelite.com/92/how-to-fix-the-ubuntu-clipboard-problem)
</code>

Glipper (Gnome) and Klipper (KDE) don't support graphical data which is something I need so I'll have to keep looking.

Chris

---

