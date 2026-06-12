---
title: "Live USB Blank Screen"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by virtualsamana on 2009-08-06
My girlfriend and I were just becoming Ubuntu converts (from Windows). We have been using the live USB until she is certain that she wants to install it on her laptop. Everything has been pretty darn peachy until very recently the screen goes blank right after the Ubuntu Splash screen completes and the Ubuntu jungle sample plays. A small window in the bottom right of the screen displays the following:

"the configuration defaults for the gnome power manager has not been installed correctly"

Since I was using the USB with persistance I was able to add some programs and shortcuts, plus edit some documents. Has all of this been lost? Is there a way to recover this USB without reloading Ubuntu again?

I am using 8.10
with a Dell Latitude D600

Thanks for any help you could provide. BTW I am an ubuntu novice so assume I know nothing cause that's about right.

---

### Post by nothingspecial on 2009-08-06
Try logging into recovery mode and typing

```
sudo dpkg --configure -a
```

---

### Post by virtualsamana on 2009-08-06
Thanks nothingspecial,

I pressed cntrl-alt&F3 to get into terminal and then I typed sudo dpkg --configure -a.  It responded with:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 5: missing package name


When I restarted I got the same blank screen with the same error window. Not sure what to do now.

---

### Post by nothingspecial on 2009-08-06
Well I`ve not seen this error myself before but it looks like you have a broken package which needs to be fixed.

To do this you need an internet connection from the shell. Are you using wired or wireless?

*****of course there may be a simpler solution to this like deleting a config file but I don`t know it******

---

