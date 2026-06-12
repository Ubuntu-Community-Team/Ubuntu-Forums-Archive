---
title: "Dropbox icon is grey"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Fanas on 2011-05-07
My dropbox tray icon is grey, I need help making it as it's supposed to be - blue. :)
It's not a big problem, but it's driving me crazy.

---

### Post by r-senior on 2011-05-07
It's supposed to be grey, to match the other indicator icons.

---

### Post by Fanas on 2011-05-07
Even if it's true, it looks awful. There should be some way to change it.

---

### Post by r-senior on 2011-05-07
I don't know if this helps ...

[http://www.omgubuntu.co.uk/2010/05/dropbox-adds-indicator-applet-customizable-tray-icon/](http://www.omgubuntu.co.uk/2010/05/dropbox-adds-indicator-applet-customizable-tray-icon/)

Those downloads should have the old blue icons. The grey ones should be coming from /usr/share/icons/ubuntu-mono-* but I don't really know the correct procedure for replacing them.

---

### Post by AlanPorter on 2011-05-07
This is a hack that works for me...

```
sudo mv /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.svg /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.svg-DISABLED
sudo cp ~/.dropbox-dist/icons/hicolor/16x16/status/dropboxstatus-idle.png /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.png
sudo update-icon-caches /usr/share/icons/ubuntu-mono-dark /usr/share/icons/ubuntu-mono-light
dropbox stop
dropbox start

```
It'll break again when the "ubuntu-mono" package is updated.

Alan

---

### Post by AlanPorter on 2011-05-07
Oooh, a better solution...

```

cd /usr/share/icons/ubuntu-mono-dark/apps
sudo mkdir 22/UNUSED
sudo mv 22/dropbox-* 22/UNUSED/
sudo mkdir 24/UNUSED
sudo mv 24/dropbox-* 24/UNUSED/
sudo update-icon-caches /usr/share/icons/ubuntu-mono-dark
dropbox stop
dropbox start

```

Then the indicator applet will not find the mono-colored icons, and instead, it will ask the dropbox app to provide icons for it.  Those are stored in ~/.dropbox-dist/icons .

Alan

---

### Post by Fanas on 2011-05-08
> **AlanPorter said:**
> This is a hack that works for me...

```
sudo mv /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.svg /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.svg-DISABLED
sudo cp ~/.dropbox-dist/icons/hicolor/16x16/status/dropboxstatus-idle.png /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.png
sudo update-icon-caches /usr/share/icons/ubuntu-mono-dark /usr/share/icons/ubuntu-mono-light
dropbox stop
dropbox start

```
It'll break again when the "ubuntu-mono" package is updated.

Alan

I'll use this, maybe after update it will look better. :) At least of the same color as the others.

---

### Post by naser2010 on 2011-06-04
Slight typo in the above advice. It should read:

sudo mv 22/dropboxstatus-* 22/UNUSED/

and 

sudo mv 24/dropboxstatus-* 24/UNUSED/


Instead of 

sudo mv 22/dropbox-* 22/UNUSED/

sudo mv 24/dropbox-* 24/UNUSED/
Thanks for the tip. I missed the Dropbox tick and now it's back.

---

### Post by behco on 2011-08-11
> **AlanPorter said:**
> Oooh, a better solution...

```

cd /usr/share/icons/ubuntu-mono-dark/apps
sudo mkdir 22/UNUSED
sudo mv 22/dropboxstatus-* 22/UNUSED/
sudo mkdir 24/UNUSED
sudo mv 24/dropboxstatus-* 24/UNUSED/
sudo update-icon-caches /usr/share/icons/ubuntu-mono-dark
dropbox stop
dropbox start

```

Then the indicator applet will not find the mono-colored icons, and instead, it will ask the dropbox app to provide icons for it.  Those are stored in ~/.dropbox-dist/icons .

Alan


Thanks Alan. It works as a charm. (just correcting a typo).

Beco.

---

### Post by hakermania on 2011-08-11
I was also questioned about this, thanks!

---

### Post by stijnblommerde on 2012-01-29
thanks. just made the changes and the icon is blue. 
hope it will last after update.

> **AlanPorter said:**
> Oooh, a better solution...

```

cd /usr/share/icons/ubuntu-mono-dark/apps
sudo mkdir 22/UNUSED
sudo mv 22/dropbox-* 22/UNUSED/
sudo mkdir 24/UNUSED
sudo mv 24/dropbox-* 24/UNUSED/
sudo update-icon-caches /usr/share/icons/ubuntu-mono-dark
dropbox stop
dropbox start

```

Then the indicator applet will not find the mono-colored icons, and instead, it will ask the dropbox app to provide icons for it.  Those are stored in ~/.dropbox-dist/icons .

Alan

---

### Post by bocao on 2013-04-27
I just upgraded to Ubuntu 13.04 and also have the same issue about Dropbox icons. I don't like the gray ones! 

I run the code below to replace the gray icons by the blue ones. This code replaces the all gray icons by colorful ones *both* in the mono-light and the mono-dark settings. If you want to do the replacement in only of of the theme settings, run only the lines related to the one you want. (It may not be the most efficient code, but it works.)



sudo mv /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-busy.svg /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-busy.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-busy2.svg /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-busy2.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-idle.svg /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-idle.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-logo.svg /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-idle.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-x.svg /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-x.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-busy.svg /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-busy.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-busy2.svg /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-busy2.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.svg /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-logo.svg /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-logo.svg-DISABLED
sudo mv /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-x.svg /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-x.svg-DISABLED
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-busy.png /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-busy.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-busy2.png /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-busy2.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-idle.png /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-idle.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-logo.png /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-logo.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-x.png /usr/share/icons/ubuntu-mono-light/apps/22/dropboxstatus-x.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-busy.png /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-busy.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-busy2.png /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-busy2.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-idle.png /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-idle.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-logo.png /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-logo.svg
sudo cp ~/.dropbox-dist/images/hicolor/16x16/status/dropboxstatus-x.png /usr/share/icons/ubuntu-mono-dark/apps/22/dropboxstatus-x.svg
sudo update-icon-caches /usr/share/icons/ubuntu-mono-dark /usr/share/icons/ubuntu-mono-light
dropbox stop
dropbox start

---

### Post by wildmanne39 on 2013-04-27
Thread closed. Please do not post in old threads.

---

