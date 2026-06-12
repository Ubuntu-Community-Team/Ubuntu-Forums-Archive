---
title: "What are the default settings for the cosmos wallpaper slide show in 10.04?"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by chunky bacon! on 2011-01-27
Every time I search for this, the response is generally "install something else," but somehow, there are already default settings in place.  I just want to know where they are.

I go to System>>Appearance Preferences>>Background

I select "Cosmos Slideshow," and there are no "Settings" options whatsoever.  However, there must be something set somewhere already, because the wallpaper changes every once in a while.

This is why I don't want to install something else, because something is already installed, controlling the settings, somewhere.  I just want to know where that is?

---

### Post by cariboo on 2011-01-28
There are no gui settings for the slide show. You have to edit /usr/share/backgrounds/cosmos/background-1.xml.

There is an easier way though, have a look [here]("http://www.howtogeek.com/howto/25549/how-to-create-a-wallpaper-slideshow-in-ubuntu/")

---

### Post by chunky bacon! on 2011-01-28
> **cariboo907 said:**
> There are no gui settings for the slide show. You have to edit /usr/share/backgrounds/cosmos/background-1.xml.

There is an easier way though, have a look [here]("http://www.howtogeek.com/howto/25549/how-to-create-a-wallpaper-slideshow-in-ubuntu/")

Thank you very much!  The xml file is exactly what I was looking for.

---

