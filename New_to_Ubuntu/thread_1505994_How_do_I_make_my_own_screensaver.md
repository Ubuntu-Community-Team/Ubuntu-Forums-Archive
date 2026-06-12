---
title: "How do I make my own screensaver?"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-09
An easier way. I read through the xscreensavers install.hacking file and it requires knowing how to code which is something I have limited knowledge on. Is there something I can use that will turn a video into a screensaver?

---

### Post by angry_johnnie on 2010-06-09
It's been about a year and a half since the last time I used KDE, but I remember it used to be able to play video as screensaver.

Maybe KDE 4 still has that option.

---

### Post by Legendary_Bibo on 2010-06-09
> **angry_johnnie said:**
> It's been about a year and a half since the last time I used KDE, but I remember it used to be able to play video as screensaver.

Maybe KDE 4 still has that option.
I have gnome though :(

---

### Post by Mr. R on 2010-06-09
But you can still run most KDE applications under Ubuntu.

Someone suggested xscreensaver, which I found in an archived thread: [http://ubuntuforums.org/showthread.php?t=529052](http://ubuntuforums.org/showthread.php?t=529052)
See if that programs works.

---

### Post by Legendary_Bibo on 2010-06-09
> **Mr. R said:**
> But you can still run most KDE applications under Ubuntu.

Someone suggested xscreensaver, which I found in an archived thread: [http://ubuntuforums.org/showthread.php?t=529052](http://ubuntuforums.org/showthread.php?t=529052)
See if that programs works.

Okay so that got me somewhere, and I copied this into my .xscreensaver file at the end of my programs file
 ```

  "Okami Credits"  mplayer -really-quiet -nosound -nolirc        \n\
                   -nostop-xscreensaver                        \n\
                   -wid $XSCREENSAVER_WINDOW                   \n\
                   -fs -loop 0                                 \n\
                   [color=red]$HOME/movies/OkamiCredits.mp4[/color]                   \n\

```
My problem is highlighted in red. I'm on Lucid and I don't think I have that directory, and when I look in the xscreensaver menu I have an Okami Credits option and an OkamiCredits.mp4 and when I looked in advanced to look at the commands, it seems they're separated like so.

---

### Post by Legendary_Bibo on 2010-06-10
Well I can get an error message now, but it only shows up when I go to preview the screensaver.

---

### Post by Legendary_Bibo on 2010-06-10
Anyone? I've been working on this all night.

---

### Post by Legendary_Bibo on 2010-06-10
Okay I got it to work! Apparently I needed to give the file permission to be executed...*sigh* that just causes problems for newbie people.

---

### Post by darolu on 2010-06-10
> **Legendary_Bibo said:**
> My problem is highlighted in red. I'm on Lucid and I don't think I have that directory
**$HOME** = your home directory, it is a 'shortcut' to "/home/<user>".
In a terminal type this so you can see it:
```
echo $HOME
```

---

