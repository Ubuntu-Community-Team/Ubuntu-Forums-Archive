---
title: "Firefox view"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by PegM_4 on 2010-02-09
I just installed UBUNTU a couple days ago and can't find settings to show all colors in Firefox.  The 2 images below show what I am seeing.  The first one is UBUNTU and the second is what I see in VISTA.  I should also let you know that this isn't a dual boot system, but images from 2 different computers, if that makes a difference.

                                   
[IMG]http://dl.dropbox.com/u/643170/Ubuntu%20Screengrab._.jpg[/IMG][IMG]http://dl.dropbox.com/u/643170/Vista%20Screengrab._.jpg[/IMG]

Thanks for any suggestions.
Peg

---

### Post by NightwishFan on 2010-02-09
You might have images or javascript disabled. Do you have noscript installed?

---

### Post by warfacegod on 2010-02-09
Did it look like that the first time you ran Firefox or did this start later?

---

### Post by PegM_4 on 2010-02-09
JavaScript is enabled.  The advanced settings are as follows:  CHECKED "Move or resize existing windows" and "Disable or replace context menus."  The rest are UNCHECKED.

I do not have noscript installed.

Yes, it has looked like this from the installation.

---

### Post by mikewhatever on 2010-02-09
Go to Edit->Preferences->Content, click Colors, and make sure the following box is checked 'Allow pages to use their own colors, instead of my selection above'.

---

### Post by NightwishFan on 2010-02-09
I just tested that page and it works on my install. The closest I could get to it looking like that was disabling images, however, you still have a few in your screenshot. Puzzling.. 

Did you alter any settings from the default?

---

### Post by warfacegod on 2010-02-09
I wonder if a simple solution here is to reinstall it.

```
sudo apt-get purge firefox

sudo apt-get install firefox
```

Make a backup of your bookmarks if you care to keep them.

---

### Post by speedwell68 on 2010-02-09
Have you tried it in any other browsers on the Linux system?  Try seamonkey...

```
sudo apt-get install seamonkey
```

What version of Firefox are you runnning on each system?

Edit: What version of Ubuntu are you running?

---

### Post by PegM_4 on 2010-02-09
> **mikewhatever said:**
> Go to Edit->Preferences->Content, click Colors, and make sure the following box is checked 'Allow pages to use their own colors, instead of my selection above'.

Thank you, that fixed it.  I don't remember changing that, but must have by mistake.  I'm my own worst enemy.  Thank you so much.

Peg:oops:

---

### Post by Paddy Landau on 2010-02-09
One more thing.

Go to Edit > Preferences > Content, and ensure that *Load images automatically* is checked.

---

