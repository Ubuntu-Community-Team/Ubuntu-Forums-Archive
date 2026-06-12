---
title: "background transparency"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by dzon65 on 2009-09-03
Hi.I posted this before but...How can I add transparency to the background options of the "pictures"-window.Saw this linux desktop once with this "sunglass"background.Not the window,only the background.

---

### Post by 3rdalbum on 2009-09-03
Do you want a transparent desktop background, or a transparent window background?

---

### Post by alienclone on 2009-09-03
sounds like they are looking for something like a way to put a faded image as the window background in their pictures folder window.

---

### Post by dzon65 on 2009-09-04
Not the desktop,only the background in for example,the pictures map.For now,there's the option to change the background with patterns,colors,adding emblems.I'm looking for a way to add transparency to those options.So not the desktop,nor the windows,just the background(like the option transparency for a terminal window).

---

### Post by dzon65 on 2009-09-04
Perhaps this explains it better. [http://images.google.be/imgres?imgurl=http://marlonpalmas.files.wordpress.com/2008/11/glass-for-vista-by-fediafedia.png&imgrefurl=http://marlonpalmas.wordpress.com/2008/11/06/glass-for-vista/&usg=__NGofnS7amGv5gnEOeXPhhuCLoDs=&h=900&w=1440&sz=2107&hl=nl&start=1&tbnid=QkNxGO7cdUupzM:&tbnh=94&tbnw=150&prev=/images%3Fq%3Dglass%2Bfor%2Bvista%26gbv%3D2%26hl%3Dnl%26sa%3DG](http://images.google.be/imgres?imgurl=http://marlonpalmas.files.wordpress.com/2008/11/glass-for-vista-by-fediafedia.png&imgrefurl=http://marlonpalmas.wordpress.com/2008/11/06/glass-for-vista/&usg=__NGofnS7amGv5gnEOeXPhhuCLoDs=&h=900&w=1440&sz=2107&hl=nl&start=1&tbnid=QkNxGO7cdUupzM:&tbnh=94&tbnw=150&prev=/images%3Fq%3Dglass%2Bfor%2Bvista%26gbv%3D2%26hl%3Dnl%26sa%3DG) Without the window transparency,just the background.

---

### Post by 3rdalbum on 2009-09-04
What you want is called RGBA support. It requires four things:

1. A copy of the Murrine theme engine, compiled with RGBA support
2. A Murrine-based theme with RGBA (most Murrine themes can be modified)
3. A compositing window manager (like Compiz or Kwin4)
4. Programs that have been built with RGBA support, or that can be patched, or that have plugins for RGBA.

I don't know if the version of Murrine in Ubuntu has RGBA support, but traditionally people have compiled it from the Murrine SVN; if you've compiled anything before it's easy.

You can get Murrine themes from [www.gnome-look.org](www.gnome-look.org), and Murrine ships with a couple. You may need to add a line or two to them to enable RGBA.

The only program that ships with Ubuntu that comes with RGBA support out-of-the-box is the Gnome system monitor. You can download plugins for Rhythmbox and Gedit to enable RGBA on those programs. For most other programs you will need to apply a source code patch from the Murrine website. Not all programs have patches available. Few program developers are interested in RGBA.

The end result looks nice, but the effort does not justify the result, even if you're just working with those easy programs. For some reason there don't seem to be HOWTOs available (not enough people interested?), but this is the closest topic I can find about it:

[http://ubuntuforums.org/archive/index.php/t-881836.html](http://ubuntuforums.org/archive/index.php/t-881836.html)

Also look at the Murrine website:

[http://www.cimitan.com/murrine/](http://www.cimitan.com/murrine/)

Good luck.

---

### Post by dzon65 on 2009-09-04
Yeah,thought it should be shipped with css rgba.I'll check into that murrine and see what I can do.Thanks for the advice,J.

---

### Post by dzon65 on 2009-09-05
Trying to find my way around those murrine-themes.Did a little test however.I added a transparent png to colors/patterns.Unfortunately,although it "works",it'll take the background as well.For instance,when you place the png on your desktop,and apply it from there,it'll pop up with a piece of the desktop wallpaper.If you try it out from the patterns-window,it'll show the background color of that window background.So,it doesn't recognize the png as being,how to say,independent.(?)

---

### Post by 3rdalbum on 2009-09-05
> **dzon65 said:**
> Trying to find my way around those murrine-themes.Did a little test however.I added a transparent png to colors/patterns.Unfortunately,although it "works",it'll take the background as well.For instance,when you place the png on your desktop,and apply it from there,it'll pop up with a piece of the desktop wallpaper.If you try it out from the patterns-window,it'll show the background color of that window background.So,it doesn't recognize the png as being,how to say,independent.(?)

That's not how it works. Remember, you need the program to be patched in order to have transparency, and when you do, it will apply the transparency in the places where the patch-writer has deemed it should go.

You can't set a transparent PNG as the Nautilus background to make the Nautilus window transparent. If you can code a patch to implement RGBA support in the window contents, that's how you will do it.

---

### Post by kamitsukai on 2009-09-05
This is easily achieved with Bespin in KDE although slightly buggy at the moment:

> [http://forums.linuxmint.com/viewtopic.php?f=42&t=32274](http://forums.linuxmint.com/viewtopic.php?f=42&t=32274) []("http://forums.linuxmint.com/viewtopic.php?f=42&t=32274")

---

### Post by dzon65 on 2009-09-09
Well,did some searching.Couldn't find anything on the subject.Looks like there are more transparency possibilities in KDE.Like this [http://evilsidebg.deviantart.com/art/Master-Of-The-Wind-126110013](http://evilsidebg.deviantart.com/art/Master-Of-The-Wind-126110013) .Ubuntu's very new to me so..Too bad though,would be nice,pictures background,computer's background,music,videos etc...something like rgba(00,00,00,.5) but hey,one can't expect everything.Thanks for the tips.

---

### Post by alienclone on 2009-09-11
> **dzon65 said:**
> Well,did some searching.Couldn't find anything on the subject.Looks like there are more transparency possibilities in KDE.Like this [http://evilsidebg.deviantart.com/art/Master-Of-The-Wind-126110013](http://evilsidebg.deviantart.com/art/Master-Of-The-Wind-126110013) .Ubuntu's very new to me so..Too bad though,would be nice,pictures background,computer's background,music,videos etc...something like rgba(00,00,00,.5) but hey,one can't expect everything.Thanks for the tips.

well you know you can have both dont ya? Ubuntu + KDE = Kubuntu

```
sudo apt-get install kubuntu-desktop
```

i personally prefer Gnome, but i hear that KDE has a lot more personalization options.

---

### Post by dzon65 on 2009-09-11
Yes,I know.And as far as I have seen,especially concerning transparency,KDE has indeed more to offer.But,I'm pretty sure someone will come up with a patch for ubuntu...I hope.

---

