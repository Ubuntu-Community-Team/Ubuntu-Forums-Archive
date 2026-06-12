---
title: "Install Gtk themes?"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by bobin on 2010-03-08
I know this sounds dumb but whenever i try to install a theme a error message comes " this does not appear to be a valid theme"" Can't move directory over directory"
[URL="http://www.deviantart.com/download/154370905/Zee__GTK_Theme___1_3_by_Simmeson.gz"]
http://www.deviantart.com/download/154370905/Zee__GTK_Theme___1_3_by_Simmeson.gz[/URL]

[Light theme]("http://launchpadlibrarian.net/40250925/light-themes_0.1.5.4.tar.gz")

---

### Post by elliotn on 2010-03-08
Extract the theme parkage and reparkage it. It worked for me previously

---

### Post by Method X on 2010-03-08
Look, its a .gz file.

Open it in archive manager, and unzip Zee__GTK_Theme___1_3_by_Simmeson archive to your home directory. Now open unzipped archieve and unzip Zee foder to your home directory.

After that open terminal and type:

```
sudo cp -r Zee /usr/share/themes/

rm -r Zee
```

Open your appearance options, go to customise and find installed style.

;)

---

### Post by bobin on 2010-03-08
Nope . no luck . Can someone try out the zee theme. (Got the Light theme to work)

---

### Post by Method X on 2010-03-08
> **bobin said:**
> Nope . no luck . Can someone try out the zee theme. (Got the Light theme to work)

Ok, try dropping to appearance properties window this attachment

---

### Post by bobin on 2010-03-08
Error "Can't copy directory over directory"

Just noticed . There are quite a few murrina themes in /usr/share/themes that are not appearing in the appearance window

---

### Post by Method X on 2010-03-08
> **bobin said:**
> Error "Can't copy directory over directory"

This means that you already installed Zee theme.

> **bobin said:**
> Just noticed. There are quite a few murrina themes in /usr/share/themes that are not appearing in the appearance window

Now try to open Appearance->Customise...->locate for Zee theme

Strange but previous method worked for me.

Ok, if it doesn't work, please post here output of *ls -l /usr/share/themes/* command.

Then go to /usr/share/themes/Zee/:

*pushd /usrshare/Zee*

and  

[I]ls -l
[/I]
and please post result here

---

### Post by bobin on 2010-03-08
cool first worked thanx

---

### Post by Method X on 2010-03-08
> **bobin said:**
> cool first worked thanx

Sweet ;)

---

