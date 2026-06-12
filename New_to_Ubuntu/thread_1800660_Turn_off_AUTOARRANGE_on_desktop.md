---
title: "Turn off AUTOARRANGE on desktop"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by jfbooth on 2011-07-09
This is XUBUNTU 11.04.  When I drag a desktop icon, it snaps back to its original position.  Is there a way to turn this 'autoarrange feature' off?

Also, if the icon NAME is too long, all that displays is part of the name.  Mousing over the icon does not reveal the entire name.  I have to right click ... which opens a window that is not needed.  By that, I mean in order to see the full name, you must perform a click which reveals the full name but opens a (properties) window that is not desired.

Any help/comment is appreciated in advance.

EDIT:  Wow!!  Xubuntu is amazing.  Apparently, if something is not working, post about it in the forum and it fixes itself!!  After making this post, I tried moving icons and IT WORKS (NOW).  Absolutely amazing.

Still, would really be nice to see the full icon name without having to open a window.

---

### Post by dcsoldschool53 on 2011-07-09
This is to stop auto arranging. I do not have Xubuntu, but this is what I do in Ubuntu. I open nautilus, and click on Desktop. From inside nautilus Desktop, right click, and look for arrange items. Click manually, or something like that. It should some your problem.

To do the same thing from the nautilus  tool bar, click View > Arrange items > manually

---

### Post by jfbooth on 2011-07-22
> **dcsoldschool53 said:**
> This is to stop auto arranging. I do not have Xubuntu, but this is what I do in Ubuntu. I open nautilus, and click on Desktop. From inside nautilus Desktop, right click, and look for arrange items. Click manually, or something like that. It should some your problem.

To do the same thing from the nautilus  tool bar, click View > Arrange items > manually

I take it nautilus is a file manager.  Xubuntu uses THUNAR.  When I follow your tip with THUNAR, there are no such options.  Thank you, though for your input.

As I mentioned, my icons snapped back ... and now they don't.  I did not do anything except make my first post ... HONEST!!

There is still the issue of the icon TITLES.  If more than one line long, they are truncated.  Would be nice if mousing over would reveal the full name.  As it is, mousing over reveals TYPE, SIZE, LAST MODIFICATION DATE but not the full icon title.

Wish I could tell this thread what I did to stop autoarrange, ... but I did not do anything .. it somehow stopped mysteriously.

---

### Post by hhh on 2011-07-22
I thought I had read somewhere that the text truncation was not fixable, but have a look at this thread, it provides a sort-of half solution...
[http://forum.xfce.org/viewtopic.php?id=6097](http://forum.xfce.org/viewtopic.php?id=6097)

Hope that helps.

---

### Post by jfbooth on 2011-07-22
> **hhh said:**
> I thought I had read somewhere that the text truncation was not fixable, but have a look at this thread, it provides a sort-of half solution...
[http://forum.xfce.org/viewtopic.php?id=6097](http://forum.xfce.org/viewtopic.php?id=6097)

Hope that helps.

I took a (quick) look at that link.  Doesn't appear to be quite 'straight forward', but will go back and read it closely.  If I can succeed, will close this thread as solved.  Thank you very much for the link.

Edit:  Thank you again .. but that is all way over my head.

---

### Post by hhh on 2011-07-22
No problem, it's not difficult, just some of the options either never worked or don't work in Xfce 4.8. It's asking you to create the hidden file .gtkrc-2.0 in your /home/[USER_NAME] folder, copy/paste the options into it and then play with the settings. It looks like the key setting to make the icons look like the screenshot in post 3 is...```
style "xfdesktop-icon-view" {
    XfdesktopIconView::cell-text-width-proportion = 5
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```
I can't test this as I won't be at my Xfce desktop until Sunday or Monday (I'm housesitting) and also I use Xfce 4.6 -I think Xubuntu 11.04 uses Xfce 4.8 .

---

### Post by jfbooth on 2011-07-22
> **hhh said:**
> No problem, it's not difficult, just some of the options either never worked or don't work in Xfce 4.8. It's asking you to create the hidden file .gtkrc-2.0 in your /home/[USER_NAME] folder, copy/paste the options into it and then play with the settings. It looks like the key setting to make the icons look like the screenshot in post 3 is...

```
style "xfdesktop-icon-view" {
    XfdesktopIconView::cell-text-width-proportion = 5
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```

I can't test this as I won't be at my Xfce desktop until Sunday or Monday (I'm housesitting) and also I use Xfce 4.6 -I think Xubuntu 11.04 uses Xfce 4.8 .

OK, .. thank you immensely for this and the private message you sent me.  This has worked, thanks to your clear and concise instructions.

The value of 5 increased the 'title width'.  I do not know what the default is, but the title 'box' is wider than b4.  I am assuming >5 widens and <5 narrows.

With thanks to you, I will mark this SOLVED.  It DOES leave me to wonder though if there is a way to have more than one line of text in the box.  That is perhaps best left to a new thread.

Thank you again.  You Gurus are the greatest.

---

