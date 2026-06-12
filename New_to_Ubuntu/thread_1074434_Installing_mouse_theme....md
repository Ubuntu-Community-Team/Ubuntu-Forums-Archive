---
title: "Installing mouse theme...?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by sdim on 2009-02-19
Hi,everyone.
How can I use a set of mouse themes downloaded and extracted into usr/local/share/icons?
I'm using Compiz & Emerald Theme Manager.
Tried by right-clicking->Change Desktop Background/Theme/Customise/Pointer,but I don't see the recently extracted mouse themes.
Many thanks.

---

### Post by RomeReactor on 2009-02-19
Hi. Where did you download the theme from? If you got it from [Gnome-Look]("http://gnome-look.org/index.php?xcontentmode=36"), you don't need to extract the package; instead, go to 'System->Preferences->Appearance->Theme' and click on "Install"; then navigate to where the package is located. After it's installed, you can then change the cursor theme.

---

### Post by sdim on 2009-02-19
Thanks for the answer.
It was from KDE Looks.org->[http://www.kde-look.org/index.php?xsortmode=high&page=0&xcontentmode=36]("http://www.kde-look.org/index.php?xsortmode=high&page=0&xcontentmode=36")
Obsidian theme.

---

### Post by sdim on 2009-02-19
It was installed but it only shows when Compiz is turned off.
Can it show with Compiz on?

---

### Post by RomeReactor on 2009-02-19
> **sdim said:**
> It was installed but it only shows when Compiz is turned off.
Can it show with Compiz on?

If it was [this one]("http://www.kde-look.org/content/show.php/Obsidian+Cursors?content=73135&PHPSESSID=be0880d90c153863a03513b9c9930927"), the instructions call for extracting to **~/.icons**. You might also want to post there.

---

### Post by sdim on 2009-02-20
> **sdim said:**
> Hi,everyone.
How can I use a set of mouse themes downloaded and extracted into usr/local/share/icons?
I'm using Compiz & Emerald Theme Manager.
Tried by right-clicking->Change Desktop Background/Theme/Customise/Pointer,but I don't see the recently extracted mouse themes.
Many thanks.

As quoted above,I've already extracted it into /icons.
The thing is that with Compiz on,I don't see the theme in the Appearance->Customise->Pointers dialog.

---

### Post by RomeReactor on 2009-02-20
> **sdim said:**
> As quoted above,I've already extracted it into /icons.
The thing is that with Compiz on,I don't see the theme in the Appearance->Customise->Pointers dialog.

I meant this (from the [icon theme page]("http://www.kde-look.org/content/show.php/Obsidian+Cursors?content=73135&PHPSESSID=be0880d90c153863a03513b9c9930927")):
> **Installation**
Either install through whatever means your desktop's theme settings has or simply extract the archive to ~/.icons/
And this:
> **Note**
KDE users please note that installing the theme through the control center can cause some cursors to use the default X cursors. To fix this simply extract the theme directly to ~/.icons/ 

Not in **/usr/local/share/icons**, but in **/home/sdim/.icons**, assuming your username is sdim. However, I don't use themes for Compiz or Emerald, or icon themes for them, so I can't assure you it will work.

---

### Post by sdim on 2009-02-20
Thank you.
I am a Gnome user,so I'll see if it works.
Many thanks for your answers.

---

