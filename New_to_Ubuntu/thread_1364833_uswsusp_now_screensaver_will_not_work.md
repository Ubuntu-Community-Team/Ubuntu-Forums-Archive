---
title: "uswsusp now screensaver will not work"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by cosine352 on 2009-12-26
okay here is what I have done 

> sudo apt-get install uswsusp

After you install uswsusp, you need to tell Ubuntu to use it as the default hibernate mechanism. To do this, open /etc/pm/config.d/00sleep_module in your favorite text editor, uncomment the bottom line, and set it to uswsusp.

SLEEP_MODULE="uswsusp"


I found this in somewhere in the Ubuntu forum. It worked very well for Hibernation (now I can hibernate in around 45 S with open virtualbox and many applications and can wake up around the same time :guitar::guitar:). But now my system will not go to screen saver. Actually screen saver sometimes work sometimes does not. 
I am not sure if I am doing something wrong. 
Any help will be appreciated.

---

