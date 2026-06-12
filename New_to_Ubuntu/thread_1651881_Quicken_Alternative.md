---
title: "Quicken Alternative"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by hermanj04 on 2010-12-23
Hello,

I am brand new to ubuntu (only had it for two days), and so far it has been wonderful.  Everything runs so much faster on this 7 year old desktop than it did under Windows.  I have been searching for alternatives to some of the programs I used on Windows.  One of those is Quicken.  I liked Quicken for its ability to attach image files to transactions.  I have tried several of the programs in the repos (KMyMoney, GnuCash, Eqonomize, and Grisbi) and I have not been able to find one that has this feature built into it.  Also, I tried running Quicken in Wine, but that did not work either.  Does anyone know of a program that I can use that has this feature?

Thanks,
Jim

---

### Post by A_M_S on 2010-12-23
Try this [link]("http://www.linuxalt.com/")


Hope that helps

---

### Post by lkraemer on 2010-12-23
You didn't mention what version of Quicken, but it won't make much
difference.........

Just purchase Crossover by Codeweavers, and then install Quicken in a
Bottle, and then copy your existing Quicken file to:
.cxoffice/win98/drive_c/program files/quicken/

It will work perfectly.  Best money you will spend.....

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Compatibility:
[http://www.codeweavers.com/compatibility/](http://www.codeweavers.com/compatibility/)

Also, there is a Java program named MoneyDance that I am using
that is somewhat similar to Quicken.  In fact I am running it in
parallel with Quicken for over a year now, while I try to make my
final decision......... Plus & Minus to both packages.........
[http://moneydance.com/](http://moneydance.com/)

Also REF:
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

lk

---

### Post by hermanj04 on 2010-12-24
Thank you for the help.  The two reference pages didn't help much for this program (I'd tried all the ones listed), but the certainly will help as I search for other programs!

I'm currently running Quicken 2010 Home & Business on Windows Vista.  Will upgrade to 2011 if I decide to continue running it.

I downloaded and used the trial of Moneydance.  It would be nice to not have to pay for upgrades every year, but I really like being able to scan receipts/warranties/etc. and attach them to the transaction before filing them.  I could try doing it and saving them in a pdf format and such, but that wouldn't be quite as convenient.

I tried running Quicken in CrossOver.  I have it running, and everything seems to be running fine with it.  However, I cannot figure out how to get a menu or desktop link to it.  Every time I want to open it, I have to go through the menus to find the qw.exe file.  I wouldn't have a huge problem with that, but the other people who input transactions would probably never be able to find it.

---

### Post by lkraemer on 2010-12-24
I'm running Quicken 2004, and during the install, it asks if I want 
a Desktop Icon and a one for the Task Bar.  I ONLY select Desktop.
Then I just use that to run Quicken.  Even the correct Icon image is there.

You can always right click on the Desktop and create one, and add
the Quicken Icon.

lk

---

### Post by hermanj04 on 2010-12-24
I must not have seen the options during the install.  I'm trying to use "Create Launcher" off of the desktop, but when I do, it doesn't do anything when I double-click on it.  Yet when I go through the File Browser I can double click and the same file runs.

---

### Post by lkraemer on 2010-12-24
OK, your Quicken Data files will be located at (Use CNTL H to Toggle the HIDDEN .cxoffice folder from /user/loginuser):
```

/home/loginuser/.cxoffice/bottle_name/drive_c/Program Files/Quicken/MYDATA*

```
if your data file is by default named MYDATA*  .....otherwise they
will be named what your requested.


My Command to launch the software is:
```

"/home/loginuser/.cxoffice/bottle_name/desktopdata/cxmenu/Desktop.C^5E3A^5Fusers^5Fcrossover^5FDesktop/Quicken+2004"

```
but, once again yours may be different.  Change as loginuser &
bottle_name as needed.


When you left click on the default icon you are here:
```

/usr/share/icons/hicolor/scalable/apps/gnome-panel-launcher.svg

```
I changed that location to point to where I had stored the Quicken.ico
which is attached in the zip file.

Just be sure to change your permissions to:
Permissions -> Allow executing file as a program
when you right click on the Desktop Icon.

Quicken should then launch from the Desktop.

This should have been automatically built by Crossover during the install.

You can also Run the crossover MANAGE BOTTLE application, DELETE the
QUICKEN Bottle, Then Re-Install Quicken.  You most likely will have to
go through the install process twice, to get Quicken installed.
I've seen this several times.  The first time through it acts as if it 
can't find some of the stuff, but still creates what it needs to find on
the second time through.  That is a poor explanation, but it sure works
that way for me.  (Licensed Crossover Pro 9.x)
OH, and you can also install other software in this Quicken Bottle, if needed,
but I try to keep each application in their own bottle, with an exception or two.

So, now you can copy the five MYDATA*.* files from Windows to Ubuntu and start
right where you were with Windows.  If you have trouble, when you exit Quicken,
tell it to backup to a Flash Drive and then copy that file to the previous
posted location in the Bottle.  Then run Quicken and Import it. 
Zit Zot!  Slick'er than SNOT!

lk

---

### Post by dmaxel on 2010-12-24
If you can't find a way to run Quicken through Wine or anything similar, I'd recommend MoneyDance if you're willing to spend a little money, or there's always GnuCash.

---

