---
title: "Nautilus Toolbar?"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by benerickson1 on 2010-08-08
Hi. Is it possible to remove text from the Nautilus main toolbar?  I would like to see the buttons only, with no words such as "Back" and "Forward". Thanks, this is kinda driving me nuts.

---

### Post by SpockVulcan on 2010-08-08
I just looked around in any view settings. I do not see anything about removing that text. Sorry...

---

### Post by Linye on 2010-08-08
I think you're better off using Nautilus Elementary. You have nothing to lose and a lot to gain visually (like customizing the toolbar). 

[http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html](http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html)

---

### Post by inameiname on 2010-08-08
Personally I use Nautilus Elementary which removes them already, but in the normal Nautilus you can change it by going in the configuration editor and going to desktop -> gnome -> interface and changing the toolbar_style I believe:

Since I use nautilus elementary I can't just do it and see as it automatically removes them, but I think it's this, which is a shortcut to the above using the terminal. Just put this in it:


gconftool-2 --set /desktop/gnome/interface/toolbar_style --type string "icons"

---

### Post by DownTown22 on 2010-08-08
Another vote for Nautilus Elementary.  Once you switch over, you'll know how you lived without it.

---

### Post by inameiname on 2010-08-08
Haha, seems we all vote for nautilus elementary instead. And here I'll make it easy for you if you want to check it out:

Just copy and paste these lines in the terminal:

sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get upgrade
nautilus -q
nautilus & exit

---

### Post by benerickson1 on 2010-08-09
Thanks for the responses.  Well I got Nautilus Elementary and it solved the issue.  I didn't mention it before but another thing that bothered me was the size of the toolbars.  Now it's a lot more compact and looks waaay better.  Thanks!!

---

### Post by inameiname on 2010-08-09
Cool. Oh, and don't forget to change the look of the breadcrumbs too, if you desire. Here are the links to the two most popular breadcrumbs hacks out there (both rock, but I prefer Clem's due to it's slim elegance). Just makes Nautilus look even cooler:


For Gnaag's:

[http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html](http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html)

For Clem's:

[http://www.webupd8.org/2010/07/victory-yet-another-nautilus-elementary.html](http://www.webupd8.org/2010/07/victory-yet-another-nautilus-elementary.html)

Also, don't forget to mark this thread as solved so it might benefit others with a similar issue (as easy as clicking 'Thread Tools' and then 'Mark as Solved' in the upper right on this page).

---

