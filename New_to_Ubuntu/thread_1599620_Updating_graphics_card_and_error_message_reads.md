---
title: "Updating graphics card and error message reads:"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by SunEatsMoon on 2010-10-18
"gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

I downloaded the updater from the ATI site and this got that message when I tried to run it.
Help please.:)

---

### Post by P4man on 2010-10-18
you are doubleclicking the installer, thats not how it works, as its a shell script.

However, you shouldnt do it this way in ubuntu. Just go to system > administration > additional drivers. If there is a driver for your videocard, it should be listed there.

---

### Post by SunEatsMoon on 2010-10-18
I see, that makes more sense.
I tried finding it under System>Administration>Hardware Drivers and nothing comes up for it.

---

### Post by P4man on 2010-10-18
Then most likely your videocard is no longer supported by ATI, and you should just use the opensource ones installed by default. Which videocard do you have?

---

### Post by Mark Phelps on 2010-10-18
If you don't know the specific make and model of your video card, you can find out by opening a terminal and entering "lspci".  Look for a line containing "VGA".

---

