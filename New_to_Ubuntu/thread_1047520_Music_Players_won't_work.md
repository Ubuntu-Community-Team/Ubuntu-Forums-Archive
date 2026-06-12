---
title: "Music Players won't work"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by rpete88 on 2009-01-22
I'm absolutely new to Ubuntu so I'm not quite sure where to start.  I'm trying to play my music files through Amarok, but it freezes every time I try to play them.  I've also tried Rhythmbox and it freezes too.  They used to play for a while and then freeze, but now it's not playing at all.  Does anyone have any suggestions?

---

### Post by Ben Page on 2009-01-22
Try with SuperUbuntu, for a first time user its excellent! All players, codecs etc are preinstalled, so no trouble with burning DVDs, listening to MP3s, oggs, wmas, watching DVDs, watching DivX...
Just google super ubuntu..

---

### Post by mcduck on 2009-01-22
This guide should help you to get pretty much every possible media file working: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by jpoRS on 2009-01-22
Hey rpete88, welcome to the community,

Since I am guessing you want to fix the problem rather than do a completely new install, you open amarok in a terminal, try and play a song, and post the output?

If you don't know how to do that, here is a step by step:

1. Open a terminal.  Unless you set up a shortcut key, or put it in a different place, I believe it can be found under Applications>Accessories>Terminal.  It should come up with a window saying-

```
"your name"@"your computer's name":~$
```

2. To run a program from terminal (like Amarok) all you have to do is put in the program name.  In this case-

```
"your name"@"your computer's name":~$ amarok
```

3. Press Enter.  Amarok should come up as normal now, but don't close the terminal.  Not only will that close Amarok, but we need the information in the terminal.

4. Try and play a song in Amarok.  It should freeze as normal.

5. Go back to the terminal.  Hopefully what is causing the problem will show itself in the output.  To copy the information you have to use Shift+Ctrl+C (the shift is important).  

6. After that post the information here, and if you can wrap it in "code" tags (look for the pound sign up in the top right corner of the "Reply to Topic" window.

Let me know if that isn't clear, and good luck!

Peace,
jim

---

### Post by markbuntu on 2009-01-22
Since you are new to Ubuntu, you would probably like some explanation about how to use your sound applications and the stuff that controls the sound and all the extras people keep telling you that you need


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by rpete88 on 2009-01-24
Here's the output after running amarok from the terminal:
```
ryan@ryan-laptop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ca18 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ca18 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QPainter::begin: Cannot paint null pixmap

```
I should mention that music played this time.


Note: After leaving amarok open for a few hours, it stopped playing again.

---

### Post by jpoRS on 2009-01-24
I don't see anything in this that explains your problem.  Does Amarok always work when you open it from terminal?  If not try opening it in terminal again and post what comes up when it doesn't play properly.

Good Luck,
jim

---

