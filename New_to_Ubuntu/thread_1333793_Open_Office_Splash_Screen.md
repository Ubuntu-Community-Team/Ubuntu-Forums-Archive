---
title: "Open Office Splash Screen"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by bonecrusher on 2009-11-21
I'm finding Open Office to be awesome compared to the hefty price for the Microsoft Office Suite. I have installed Open Office Formula (or Math), but it doesn't appear in the applications drop down list. I have found the only way for me to access it is to launch an Open Office app, like Word Processor first and then immediately close it. This causes the "Welcome to Open Office" splash screen to appear--allowing me to choose any of the installed Open Office apps. The splash screen shows "Spreadsheet", "Text Document", "Presentation", "Database",  "Formula", "Drawing", etc. I can select "Formula" and be off to the races.
 
Is there a way to launch the "Welcome" splash screen without having to go the circuitous route of launching an app first and then closing it?

---

### Post by niteshifter on 2009-11-21
Hi,

Click System -> Preferences -> Main Menu.

In the left pane, click Office.

Look in the right pane, probably you'll see an entry for "OpenOffice.org Math". Click the checkbox to enable display.

If the entry isn't there, you can add it:

Open Main Menu like above. In the Left pane click Office. Click any item in the right pane.

Click the New Item button.

In the Create Launcher dialog, Type needs to be "Application", Command needs to be:
```
ooffice -math
```
Name and Comment it as you like.

Want a link on the desktop? Right click on the desktop, click Create Launcher. Fill in like above.

And last, to invoke it from the command line - you've probably already guessed it ;) - type:
```
ooffice -math
```

---

### Post by bonecrusher on 2009-11-22
Thanks, Niteshifter.  That solves it for me.

---

### Post by Hagar Delest on 2009-11-22
Else, you can get the Start center by creating a launcher pointing to /usr/bin/openoffice.org3. (I've that with the Sun version, should be the same for the Ubuntu version of OOo I guess).

---

