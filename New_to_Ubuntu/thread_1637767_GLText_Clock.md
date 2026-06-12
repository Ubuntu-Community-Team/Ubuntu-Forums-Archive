---
title: "GLText Clock"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by zer010 on 2010-12-04
This one seems to have been done to death, but I still can't seem to get a clock going.  I had done it in Jaunty, but no matter how I configure it, it's not working in Lucid!
One issue I've found in the many threads and how-to docs is that everyone says that it's only a matter of adding the options to this line in /usr/share/applications/screensavers/gltext.desktop:
```
Exec=gltext -root
```However, my gltext.desktop looks like this:
```
[Desktop Entry]
Name=GLText
Exec=/usr/lib/xscreensaver/gltext -root
TryExec=/usr/lib/xscreensaver/gltext
Comment=Displays a few lines of text spinning around in a solid 3D font. The te$
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver
OnlyShowIn=GNOME;
```
I've tried adding my time options to "Exec=..." and then to "TryExec=..." lines, but to no avail.  What am I missing here?

---

### Post by conradin on 2010-12-05
lowercase exec?
exec=gltext

---

### Post by zer010 on 2010-12-05
Why ask me?  I have no clue! :lolflag:
Are you suggesting that I add that as a new line or replace a line with that?

---

### Post by gmargo on 2010-12-05
This works for me in 10.10 Maverick:
Create a new file "/usr/share/applications/screensavers/gltime.desktop" with the following content:

```

[Desktop Entry]
Name=GLTime
Exec=/usr/lib/xscreensaver/gltext -root -text "%A\n%B %d\n%H:%M:%S"
TryExec=/usr/lib/xscreensaver/gltext
Comment=Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski.
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver;
OnlyShowIn=GNOME;

```

---

### Post by zer010 on 2010-12-05
I notice that these are the two lines that are different:
```
Name=GLTime
Exec=/usr/lib/xscreensaver/gltext -root -text "%A\n%B %d\n%H:%M:%S"
```I know that giving it a new name will make it appear as a new option in Screensavers. Thanks, I'll try that. I also see that you use double-quotes instead of single-quotes as some How-Tos suggest. The man page for gltext also uses double-quotes and I've tried both ways. Like I said, I'll give it a go and report my findings.

---

### Post by zer010 on 2010-12-05
I copied your suggestion and logged out , but to no avail. I don't have GLTime listed under my Screensaver options.  GLText, of course, is the same as it was.  Perhaps this is just a bug in 10.04?  It seems like this wouldn't be an issue though as this has been a long standing screensaver for quite some time.

---

### Post by gmargo on 2010-12-07
I got it working on 10.04 Lucid.  I added the gltime.desktop file but as you observed, the "GLTime" option does not show up in the list of screensaver choices.

What I did was install the **xscreensaver-data-extra** package.  Somehow this caused gnome to notice, and update the list, because after that, GLTime showed up in the screensaver list.  For testing, I then removed that package, but the GLTime entry remained.  I can't explain why.

---

### Post by zer010 on 2010-12-08
That's quite interesting indeed.  However, did the screensaver work as it was supposed to? 
There is perhaps a different file that controls what screensavers are listed and is updated, perhaps like grub......

---

### Post by zer010 on 2010-12-08
I haven't installed **xscreensaver-data-extra **because I noticed that it will also bring in around 20 other screensavers that I have no interest in.  There's got to be fix for this. I think I'm going to submit a bug report for this as I've tried everything ***but ***install the **xscreensaver-data-extra **package.

---

### Post by rburkartjo on 2010-12-10
gmar that is what i had to do to get in working in 10.10

---

### Post by zer010 on 2010-12-10
Ok, I broke down and installed xscreensaver-data-extra and it did work, but now I have all these extra screensavers that I don't really want.  I noticed that the packages installed were: 
```
libjpeg-progs libnetpbm10 netpbm xscreensaver-data-extra
```
How can I remove the screensavers that I don't want yet keep the gltime screensaver?
It seems that the packages other than xscreensaver-data-extra are image manipulation tools.

---

### Post by zer010 on 2010-12-10
I also noticed that every time I wanted to make a change to the gltime file it would not reflect the changes unless I uninstalled xscreensaver-data-extra, reinstalled it, logged out and then logged back in.  This seems like a really cumbersome and bloated workaround for a simple operation. At least I finally have what I want...and a whole lot more that I really don't...

---

### Post by gmargo on 2010-12-11
I don't know the whole story yet but I think it has to do with this file: **/usr/share/applications/desktop.en_US.utf8.cache**. (Your name may differ if in a different locale.)  This file contains cached copies (llke the name implies) of all the .desktop files, including the gltext.desktop file.

This would explain why your changes don't show up without installing something.

I think it has to do with **dpkg** "triggers" and the **update-desktop-database** command.  But right now I can't quite see how to regenerate that cache file.

> 
every time I wanted to make a change to the gltime file it would not reflect the changes

You can get around this by not putting the options in the .desktop file.  Instead, make the .desktop file run a shell script, and put all your options in the shell script.

---

### Post by gmargo on 2010-12-11
I was a bit off: it is the **python-gmenu** package that is triggered by dpkg to rebuild the desktop cache. The **update-desktop-database** program rebuilds the mime cache.

Here's how to force the desktop cache to rebuild:
```

$ sudo dpkg-reconfigure python-gmenu

```So, after you install or modify gltime.desktop, run the above command.

---

### Post by zer010 on 2010-12-12
Thanks, does this mean I can get rid of all those other screensavers?

---

### Post by zer010 on 2010-12-12
I just auto-removed the xscreensaver-data-extra package, logged out and when I logged back in......I still have the gltime screensaver!  Hooray!  Thanks everyone for your help.  I finally have the screensaver I want and in the way that I want it.  Thanks again, everyone! :D

---

