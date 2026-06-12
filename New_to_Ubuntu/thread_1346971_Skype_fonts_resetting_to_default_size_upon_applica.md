---
title: "Skype fonts resetting to default size upon application restart"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Anuovis on 2009-12-05
Hello,
Every time I start Skype the font size is resetted to the default 10. I can change it through Qt4 settings but this is not saved permanently. I click save, close the settings window but every time it is opened the font is back to 10.
There is no option inside Skype menus to change the fonts. 

Any hints on how to fix this?
The default font looks very small and is hard to read, so any help would be appreciated.

---

### Post by Anuovis on 2009-12-06
Bump-update

---

### Post by Anuovis on 2009-12-06
This is probably the last update as I am really out of ideas what to do...

I had two Qt config utilities, qt3 and qt4. Removed both of them and installed each individually in case there was a conflict between the two.
Looks like qt3 can save the font settings but Skype ignores it. qt4 does not save the settings but Skype takes the fonts only from there.

What do I do now? Seems so simple... And it worked the first time I installed Karmic, now out of the sudden it does not :roll:

---

### Post by Anuovis on 2009-12-08
It appears to be a [bug]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/298781").
Not much can be done now, I think. Unless somebody knows a work-around for this.

---

