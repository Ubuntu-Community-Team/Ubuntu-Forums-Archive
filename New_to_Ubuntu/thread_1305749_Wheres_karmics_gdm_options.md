---
title: "Wheres karmics gdm options"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-10-30
Maybe im being a muppet (feel free to disagree) wheres the option to change the gdm in karmic??? in login window i only have automatic login options, and sounds also, where the options to configure desktop sounds

---

### Post by MrWES on 2009-10-30
> **CaptainMark said:**
> Maybe im being a muppet (feel free to disagree) wheres the option to change the gdm in karmic??? in login window i only have automatic login options, and sounds also, where the options to configure desktop sounds

The traditional method for changing the GDM login window/theme was removed. I found this work around, but I haven't tried it as of yet.

[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html")


Bill

---

### Post by CaptainMark on 2009-10-30
thanks this is what i was looking for, maybe i wont change it if the speed suffers. New boot times are so fast

---

### Post by hambone79 on 2009-10-30
I tried the tips recommended in that link and it doesn't work. I have a custom GDM theme with my company logo that I would like to use and I can't figure out how to get it loaded.

---

### Post by falconindy on 2009-10-30
> **hambone79 said:**
> I tried the tips recommended in that link and it doesn't work. I have a custom GDM theme with my company logo that I would like to use and I can't figure out how to get it loaded.
You have a GDM 2.20 theme. It won't work with the new GDM, version 2.28.

---

### Post by CaptainMark on 2009-10-30
what about sounds then, anyone aware where theyve nipped off to

---

### Post by nwadams on 2009-10-30
i know there are system sound settings in the sound preferences now. I think those are the ones you are looking for.

Good luck and have fun :P

---

### Post by ranch hand on 2009-10-30
As far as the login box itself, lots of folks would like to know the answer.

The background image, on the other hand, resides at /usr/share/images/xspash.  There are 7 "bg" images.  bg_2560x1600 is also used by the GDM on the login screen.

These images can be replaced with any image you want as long as you scale the bugger to match the size and resolution of the image to match those already there.

I use my wallpaper image.

---

### Post by Tuxoid on 2009-10-30
I don't think it's very Linux-like to take out such customization of gdm. It wasn't hurting anything. The gdm themes were not complicated technical software, just some images, xml, and the pseudo '.desktop' file.

At the very least, the devs could add an addition gdm theme chooser for those who'd want the.

not trying to QQ, but this is messed.

---

### Post by ranch hand on 2009-10-30
> **Tuxoid said:**
> I don't think it's very Linux-like to take out such customization of gdm. It wasn't hurting anything. The gdm themes were not complicated technical software, just some images, xml, and the pseudo '.desktop' file.

At the very least, the devs could add an addition gdm theme chooser for those who'd want the.

not trying to QQ, but this is messed.
There have been a lot of changes in the basic workings of this OS.  Some of it is barely stable.  This really needs to change before a gui is going to work.

I believe that there is a gui in the works.  We may not see it until 10.04.

---

### Post by K. Hendrik on 2009-11-09
The GDM in Karmic is not that easy to configure anymore, but you can change the theme a little, I've just uploaded a GTK Theme for the GDM and a description of how to apply it at [gnome-look.org]("http://www.gnome-look.org/content/show.php/MalistaLogin?content=115158")

---

### Post by mpe on 2009-11-11
See also [http://ubuntuforums.org/showthread.php?t=1322514](http://ubuntuforums.org/showthread.php?t=1322514)

---

