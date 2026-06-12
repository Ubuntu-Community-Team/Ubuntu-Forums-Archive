---
title: "Switch to other keyboard language?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by woodyg on 2009-10-24
How can I switch to a different language for the keyboard? I need to use some international characters...

???

---

### Post by NCLI on 2009-10-24
Very simple.

Just go to System->Preferences->Keyboard. Then click the "Layouts" tab.

---

### Post by roger_1960 on 2009-10-24
Hi

System > preferences > keyboard > layouts > add .........

---

### Post by woodyg on 2009-10-24
thanks. seem to be what im looking for. But how do I implement it? I add a language under layout, but how to implement it? I can't even make it stick in the "test field"...

---

### Post by ajgreeny on 2009-10-24
Add the keyboard indicator to your panel by right clicking in an empty space -> "Add to panel" and you can quickly change layout, though you will have to have activated the alternatives you want, as above posters say.

---

### Post by woodyg on 2009-10-24
> **ajgreeny said:**
> Add the keyboard indicator to your panel by right clicking in an empty space -> "Add to panel" and you can quickly change layout, though you will have to have activated the alternatives you want, as above posters say.

sorry, I don't follow. So I close my "keyboard preferences" and click in an empty space... where? empty space where? I right click in a number of places, but nowhere do I get the option "add to panel".

---

### Post by NCLI on 2009-10-24
An empty space on your Gnome panel, the things on the top and bottom of your screen :)

Just right-click an empty part of a panel.

---

### Post by woodyg on 2009-10-25
> **NCLI said:**
> An empty space on your Gnome panel, the things on the top and bottom of your screen :)

Just right-click an empty part of a panel.

I suppose you mean the panel on the very top, containing (in my case) firefox (and any other open applications) icons to the left and icons for wireless connection, battery and sound to the right.

If I right click on the top (with keyboard preferences closed), I have the options:

Preferences
About
Remove from panel
Lock to panel (already ticked)


If I right click on the top (with keyboard preferences open), I have the options:

Move
Resize
Always on top (unticked)
Close


I must be on the wrong track, right? :confused:

---

### Post by ajgreeny on 2009-10-25
You can add an applet to either the top or bottom panel, but to do it you must right click on an **empty** part of the panel.  With the menus you have seen, you have been clicking either on an applet icon or in applet space that is already being used.

So choose an empty area of your chosen panel well away from anything else and try again.  There are lots of useful applets you might want to add and use.

---

### Post by woodyg on 2009-10-25
> **ajgreeny said:**
> You can add an applet to either the top or bottom panel, but to do it you must right click on an **empty** part of the panel.  With the menus you have seen, you have been clicking either on an applet icon or in applet space that is already being used.

So choose an empty area of your chosen panel well away from anything else and try again.  There are lots of useful applets you might want to add and use.

I think I managed something in the end... think I had this problem:
[COLOR=DimGray][I][FONT=Courier New]
There's a sort of bug with the Gnome Panel when used with Ubuntu Netbook Remix. Apparently, the only way to add applets or modify the panel at all is to right-click on a blank part of the panel. Unfortunately, UNR maximizes some of the default panel applets so that there is literally no blank space to click on.

This problem is particularly annoying because it's easy to (accidentally) remove applets and you can't get them back again. I managed to remove the battery and network monitor when I was fooling around.

So, the trick is to Alt-F1, and from the menu that pops up pick an application, right-click on it, and select "Add to Panel". This will work for ordinary apps but if you have lost the notification area (where battery and network monitors live), then there's an extra step.[/FONT][/I][/COLOR]

( [http://alanhogue.blogspot.com/2008/12/adding-applets-to-ubuntu-netbook-remix.html](http://alanhogue.blogspot.com/2008/12/adding-applets-to-ubuntu-netbook-remix.html) )

what I have managed is to get a shortcut on the top panel leading to "keyboard preferences". However, there are still 2 issues. The first and biggest one is that I still cannot change keyboard language even with "keyboard preferences". If I select a language, then nothing change. Selecting "apply systemwide" makes no difference either. I did manage to change language once... after rebooting. But I should not have to reboot right? :(

The second issue is that I would like something easy as in windows, just an easy flick on an icon... not entering complex keyboard setup menus. If I have to swap language every once in a while then it is gonna get annoying.

---

### Post by ajgreeny on 2009-10-26
It's a pity you didn't say you were using the UNR in your text, as other users may have been able to point you in the right direction straight away, and I didn't see that in the header to the post where the forum section is noted.  That is the folly of going to posts direct from the forum's RSS feed, I'm afraid.   I assumed you were on the standard gnome desktop, so I'm sorry if the info was confusing.

---

### Post by woodyg on 2009-10-27
Do you know how it works on UNR?

Otherwise, do you know how it normally works on non-UNR... do one have to enter "keyboard preferences" every time one wanna change keyboard language, or can one maybe add some simple language-switch to the panel?

---

### Post by woodyg on 2009-10-27
problem solved!!! :D

I installed KKBSwitch. great stuff! just what I was looking for...

---

### Post by wayeast on 2010-03-11
I posted this as a reply to another thread, but it belongs here as well (if anyone is still looking).

For those who want to add applets to the panel (such as the keyboard layout switcher) of a standard UNR 9.10 Gnome desktop, first right-click on the open panel (black strip at the top of the screen) and select "Remove from panel." After that, you can again right-click in the same space and select "Add to panel" to add any applet you like from the Gnome desktop.

As near as I can tell, this works this way because what appears to be the panel on an out-of-the-box installation is actually a working applet called Window Picker (you can find it in the "Add Applet" dialogue box). You must first remove this before you can get to the real panel and start adding other applets. Don't forget, though, once you've added the applet(s) you want (in my case, the keyboard switcher) and moved it/them into the desired location on the panel, to add either Window Picker or one of the other window selectors back to your panel. Otherwise you won't be able to see your running applications at all!

One other thing, in response to woodyg, though this should really be a question for someone who might know the answer.  In order to add a keyboard layout, must one first go to System->Adminstration->Languages and install language support for the keyboard setting one wants BEFORE trying to add a keyboard layout?  Or can it be done even without language support already installed?  (At the risk of sounding silly).

---

