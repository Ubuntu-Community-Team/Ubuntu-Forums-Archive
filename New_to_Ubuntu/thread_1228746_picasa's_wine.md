---
title: "picasa's wine"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by wirate on 2009-08-01
can I run other Windows programs using Wine bundled with Picasa 3.0? If yes, how?
I dont know how to use Wine alone :)

---

### Post by jacklinux on 2009-08-01
WINE and Picasa run more or less the same programs [http://www.winehq.org/help/](http://www.winehq.org/help/) might help with WINE

---

### Post by RomeReactor on 2009-08-01
Hi. As far as I know, Picasa only bundles a few of Wine's libraries, not the whole installation. An easy way to use Wine: first install it using Synaptic (or whichever package manager you like); once you have wine installed you can open a Terminal (Applications->Accessories->Terminal), write **wine**, then press the SPACEBAR once, drag and drop the executable there, and press ENTER.

The easiest way to use Wine, however, is to right-click on an exe file, select "Properties", go to the "Open With" tab, and select "Wine Windows Program Loader". Now whenever you double-click on an exe file it will run it with Wine.

You should move your Windows executables to Wine's folder; you can easily access it from 'Applications->Wine->Browse C:\ Drive'

---

### Post by Mark Phelps on 2009-08-02
If you're going to run MS Windows programs, you will save a lot of grief and frustration by first going to the Codeweavers application compatibility db site and searching for the apps and versions that you want to use:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

If you don't see any ratings for the app and version you want, or if the rating is "garbage", you're wasting your time installing Wine.

---

### Post by wirate on 2009-08-03
> **Mark Phelps said:**
> If you're going to run MS Windows programs, you will save a lot of grief and frustration by first going to the Codeweavers application compatibility db site and searching for the apps and versions that you want to use:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

If you don't see any ratings for the app and version you want, or if the rating is "garbage", you're wasting your time installing Wine.

Thanks that did save time:)

---

### Post by MrWES on 2009-08-03
> **waqar said:**
> can I run other Windows programs using Wine bundled with Picasa 3.0? If yes, how?
I dont know how to use Wine alone :)

There's a dep for Picasa 3.0, albeit beta, but no need for Wine.

I run it on my laptop and it's pretty solid.

Bill

[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb]("http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb")

---

