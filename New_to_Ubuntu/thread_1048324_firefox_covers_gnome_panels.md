---
title: "firefox covers gnome panels"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by antony_css on 2009-01-23
Can anyone help me?
The browser suddenly enlarge itself to cover the whole screen while I am surfing some webpages. I can't see the upper and lower panels. The banner of firefox is also absent.

Restarting doesn't work... dragging the bottom-right corner doesn't work also... Alt+ right mouse key and selecting "resize" does not work either. reinstalling the package does not work.

what should I do?

---

### Post by Sprut1 on 2009-01-23
Did you press F11?

---

### Post by cwsnyder on 2009-01-23
Since you say it is web page related, I am thinking it may be that your screen is too small to properly show the web page.  Do you have a screen capable of showing at least 1024x768 pixels?  800x600 or smaller is too small to properly show some web pages, and when you go to those sites or show particular graphics, it can only show part of the page.  If your video card is more capable of showing graphics than your screen, that may be what is biting you.

---

### Post by antony_css on 2009-01-23
> 
Did you press F11?

No, I didn't.
When I pressed F11, even the menu bar and the navigation bar disappear.

But strangely when I pressed it one more time, the screen somewhat re-align itself to include the gnome panels and the banner.
may be this is a bug.....

---

### Post by antony_css on 2009-01-23
how strange it can be solved this way....???

but anyway, it is solved.

---

### Post by Sprut1 on 2009-01-23
> **antony_css said:**
> No, I didn't.
When I pressed F11, even the menu bar and the navigation bar disappear.

But strangely when I pressed it one more time, the screen somewhat re-align itself to include the gnome panels and the banner.
may be this is a bug.....

Sounds strange, I have no experience with this, sorry. This is a Firefox only related problem then I figure?

---

### Post by antony_css on 2009-01-23
> Since you say it is web page related, I am thinking it may be that your screen is too small to properly show the web page. 

My monitor's size is 1280x1024, so this is not a problem....

But when you click to see some sites, an pop-up sometimes appear and cover the whole screen... It may be an adverisment... Always I have to press Alt+F4 to close it.

**EDITED: **because I can't find the [x] button on the whole screen.

But this time the problem is so series that the main browser is affected.
Is it anything related to javascripts?

---

### Post by antony_css on 2009-01-23
I mean... can javascripts change the screen size and position?

---

### Post by mirhciulica on 2009-01-23
Sometimes I get this behaviour, especially when I start Firefox.
This happens because the unmaximized window size for Firefox is to large, and some sites, control via JavaScript the window and unmaximize  it.
To fix this, you have to enable in compiz the Move window plug-in and look what key combination is set up for the movements. And then unmaximize Firefox, move it using the key combination from compiz plug-in and resize it as you like.

---

### Post by davideotape on 2009-01-23
I had this problem as well. It is nothing to do with screen size or webpage at all. Check this bug report for a solution:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99740]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99740")

---

### Post by margazhang on 2009-01-27
I get this problem fixed by renaming this file localstore.rdf in the firefox default folder to localstore_bak.rdf

---

### Post by antony_css on 2009-01-29
And it can also be solved by pressing F11 twice.

---

### Post by physeetcosmo on 2009-03-16
> **Sprut1 said:**
> Did you press F11?

Nice! Thankyou, this worked after I tried turning of visual effects and restarting the GUI. It made it small enough that I could resize it!

Does anyone know why pressing F11 does this? What is it's function?

Thanks!

---

