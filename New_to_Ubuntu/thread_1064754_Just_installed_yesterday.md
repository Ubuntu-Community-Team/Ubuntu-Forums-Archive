---
title: "Just installed yesterday"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Jimmmac1 on 2009-02-09
Good morning.

I just moved from Xandros to Ubuntu yesterday.  Outside of a few minor issues, things went well and I am up an running.  A few questions though

1.  I have 5 panes/desktops and would like a different background photo on each one.  Is this possible?
2.  I really liked Xandros File Manage, which was very much like Windows FM, but better.  For instance, to open folders, I have to click on inside the main window rather than the folder list on the left.  Is there a way to get a FM that will look like this, or can I configure the FM with Ubuntu to do this?
3. How do I automatically open a file with OpenOffice Calc?  I have a link on the app bar, and want to open a specific file when I click on the link.

I will probably have more as I go on, but really appreciate the help with these three.  Thanks.

Jim

---

### Post by johnjohn2 on 2009-02-09
Morning,

1, Yes you can but you need to disable nautilus draw desktop for this to work you must also have compiz installed and running!

Press alt+F2
Type > gconf-editor and press enter

Goto Apps,Nautilus,Preferences and then disable Show desktop.

In CCSM from system,preferences select wallpaper and configure from there

NOTE All icons you have set to be displayed on the Desktop will not be visible.

2,Try searching the ubuntu forums for help.

3, Right click the file and select Propeties and then the Open With tab and select Open Office Calc from there

Regards John

---

### Post by Jimmmac1 on 2009-02-09
Hi John

Thanks for your response.  I followed you down until I got to CCSM.  I got 2 and 3 all fixed.  CCSM?  Thanks again.

Jim

---

### Post by LowSky on 2009-02-09
CCSM is the compiz configuration tool, thats all, just type this in terminal or look up ccsm in add/remove

sudo apt-get install ccsm

---

### Post by ChildOfMana on 2009-02-09
CCSM is CompizConfig Settings Manager. It's an advanced settings manager for configuring Compiz.

Its not installed by default so open a Terminal (Applications > Accessories > Terminal) and type;

```
sudo apt-get install ccsm
```

You should now find it under System > Preferences.

As for point No. 2, are you referring to folder bookmarks? Basically a list of your favourite folders listed under *Places* in the column on the left-hand side of the File Manager? If so then go to *Bookmarks* in the File Manager (at the top) and click *Add Bookmark* and add the folder you want to bookmark. It'll then appear down the left-hand side and clicking it will open the folder directly, rather than having to drill down to it using the main window.

Obviously, if I've got the wrong end of the stick about the File Manager there then just ignore my mad ramblings ;)

Hope this helps.

---

### Post by drs305 on 2009-02-09
> **Jimmmac1 said:**
> Hi John

Thanks for your response.  I followed you down until I got to CCSM.  I got 2 and 3 all fixed.  CCSM?  Thanks again.

Jim

CCSM is the Compiz Configuration Settings Manager (CCSM). You can install it with:
```
sudo apt-get install compizconfig-settings-manager
```

To run it, either System > Preferences > CompizConfig Settings Manager or
```

ccsm &

```

---

### Post by Jimmmac1 on 2009-02-09
Hi all

Thanks to everyone for your help. I got everything pretty much set up and now know how it works.  Nice to have so many people who are willing to help out.  Have a great day.

Jim

---

### Post by johnjohn2 on 2009-02-10
> **Jimmmac1 said:**
> Hi all

Thanks to everyone for your help. I got everything pretty much set up and now know how it works.  Nice to have so many people who are willing to help out.  Have a great day.

Jim

Glad to provide some support!

Regards john


:guitar:

---

