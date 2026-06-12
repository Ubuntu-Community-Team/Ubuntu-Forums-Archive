---
title: "OpenOffice 3.0"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-01-25
I installed oo3 using the instructions [here](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml), but I can't seem to get the welcome menu where you it gives you the option to choose whether you want to open a test document, a spreadsheet, or start a presentation. I just have the same thing as 2.4, where you choose what to open from the applications>office menu. And oo's look changed too. Instead of the normal, human themed windows, I get these plain gray windows. Here's a screenshot:

[IMG]http://i93.photobucket.com/albums/l41/buck3tph0t0/OO3screenshot-1.png[/IMG]

Did I install it wrong, or do I have to download something else to get the welcome screen and to change the theme?

---

### Post by Sup3r3g0 on 2009-01-25
bump

---

### Post by blueridgedog on 2009-01-25
I think the welcome menu option is turned off on the menu by default (it is just a program option).  You can turn it on with system -> preferences -> main menu -> office then check openoffice.org.  You can also get to it by closing the window (not the app, but the document) in the image you sent.  No idea on the fonts.

---

### Post by caro on 2009-01-25
I added a drawer to the top panel and added Open Office to the drawer.  When I click on it, I can select what I want to do (spreadsheet, word processor, etc).  Just another option.

---

### Post by caro on 2009-01-25
I added Open Office to the top panel (as a drawer).  When I click on it, I can select what I want to do (spreadsheet, word processor, etc).  Just another option.

double post - mods, please remove.  Thanks!

---

### Post by Sup3r3g0 on 2009-01-25
Thanks. I was able to get the welcome screen. Still need help with the menu style.

---

### Post by SunnyRabbiera on 2009-01-25
> **Sup3r3g0 said:**
> Thanks. I was able to get the welcome screen. Still need help with the menu style.

well you might have lost the integration too if you removed open office 2 and replaced it with 3 from the open office site.
Actually the best way to install OO3 is to just remove OO again, and add this to your sources list:
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

That should give you OO3 plus the pacakges to make OO3 blend into Ubuntu better.
But if you want to you can revert to OO2 again, OO3 has no real security updates to offer and the only major thing I see it offers is .docx support but if you dont use office 2007 then you dont need OO3

---

### Post by blueridgedog on 2009-01-26
Ah...I missed that.  Yes, if you installed oo.o from the site, rather than using synaptics and the software source:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

that explains the menus that you see.

It would be an easy chore to uninstall it and reinstall it the right way.

---

### Post by Sup3r3g0 on 2009-01-26
Thanks I'll try it out.

---

### Post by Sup3r3g0 on 2009-01-27
I uninstalled oo3 by using "sudo apt-get remove openoffice*.*" I added the repoby going to system, admin, software sources, add, and then pasted the deb. I then went to add/remove and checked openoffice full productivity suit. It installed and when I opened it still has the same gray, menu style.

---

