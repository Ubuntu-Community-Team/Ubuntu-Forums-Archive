---
title: "Strange box that blocks panel."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Arpeggiator on 2011-06-07
So my sister's Toshiba Laptop has this weird box (screen shot is provided) that does not allow her to maximise her windows to the panel above. I tried moving, clicking, right clicking, and deleting it to no avail however. Any suggestions to removing it? Is there a terminal command to reset the 'default desktop'? :confused:

(screen shot again): [http://ubuntuforums.org/attachment.php?attachmentid=194466&stc=1&d=1307458813](http://ubuntuforums.org/attachment.php?attachmentid=194466&stc=1&d=1307458813)

---

### Post by dniMretsaM on 2011-06-07
It's because Docky is installed. When you first log in you'll see a message that says that Docky needs compositing to function properly. Run the codes on [this]("http://ubuntu-tutorials.com/2009/02/25/update-enable-compositing-the-easier-way/") page and you should be all set.

---

### Post by corncob on 2011-06-07
Welcome to the forums!  I use [CTRL][ALT][BACKSPACE] to reset the desktop.  You need to go to System > Preferences > Keyboard >Layouts > Options > Key Sequence to kill the X server and check your only choice.  I don't know if this does anything more that rebooting would do but its faster.  Hope it helps.

---

### Post by Arpeggiator on 2011-06-07
Thanks for the quick response guys! I will try it when I get a chance. ;)

---

### Post by Arpeggiator on 2011-06-14
I figured it out. That strange box was the 'dock'. I opened the settings manager for the dock application, clicked on the black box and clicked delete. It was a simple fix and I appreciate your help. Thanks Guys! 

~Arpeggiator~ :popcorn:

---

