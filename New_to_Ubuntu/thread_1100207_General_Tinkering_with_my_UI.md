---
title: "General Tinkering with my UI"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Frank-er on 2009-03-19
OKay so in the last 4 hours I decided it would be nifty to have a dualboot system with XP SP3 and Ubuntu (8.10). So far, not bad. I've been tinkering and enjoying this so far. So the basic sounds that come with Ubuntu are kind of annoying, and bland to be honest. No problem, so that Gnome org site place. Found some sounds, and some nifty new cursors...I can't for the life of my figure out how to install either of them! Ive been reading the beginners guide to ubuntu slowly, and its helped me, but on these two topics its giving me nothing! Any help?

Please and thanks in advance,

Franker

---

### Post by blackened on 2009-03-19
I don't think there is a GUI for installing system sounds. Sound themes are located in /usr/share/sounds. Cursor themes are located in the icon directories /usr/share/icons (for global installation) or ~/.icons (for single-user).

Extract the themes and manually move them to the appropriate directories.

---

### Post by Frank-er on 2009-03-19
So I do this through the terminal window or something? I don't know what you mean >.<

---

### Post by blackened on 2009-03-19
Practice makes perfect, and the more you use it the easier and more natural it becomes. Eventually you'll get to where you prefer doing things through the terminal.

Things to remember: 
[LIST]
[*]Folder and filenames are case sensitive. *Desktop* is not the same as *desktop*.
[*]Changing files or folders in any directory other than your home directory requires superuser (sudo) privileges.
[*]Use *cp* to copy files, use *cp -r* to copy folders.
[/LIST]

Extract the theme files that you downloaded, then use the terminal to do the moving via the cp command:

```
sudo cp -r */path/to/icon/theme/folder* /usr/share/icons
```

or

```
sudo cp -r */path/to/sound/theme/folder* /usr/share/sounds
```

---

### Post by Frank-er on 2009-03-19
Alright. Its wayyy to late in the early morning/late at night. I'm giving up. This stuff is hella harder than what I've been told and read. Perhaps I should stick with windows? /facepalm

---

### Post by blackened on 2009-03-19
Heh. It's not hard, it's just different than what you're used to. All new things have a bit of a learning curve to overcome, Linux is no exception to that rule.

---

### Post by pbpersson on 2009-03-19
I modified all my system sounds by going to:

System-->Preferences-->Sounds and on the sounds tab I chose different Hal9000 Wave files to give my Ubuntu machine a personality.  :D

---

### Post by theozzlives on 2009-03-19
The icons you can drag the tar.gz file to your themes window. Select customize > icons and they'll be there.

The sounds you go to System > Preferances > Sound and on the sounds tab you can change to a custom sound from there.

The welcome sound (drumroll at login) is set in the login window of Administration.

---

### Post by Frank-er on 2009-03-19
Okay! Sooo I figured out the sounds, apparently i'm blind as I was in the preferences > Sound menu. Didn't realize I could just import the sound there. I call jackass on my self! 

But I'm still stumped on how to get the cursors to work. Anyone able to break this down into like the super basics? Please and thank you.

Franker

---

### Post by LowSky on 2009-03-19
suprised no one mentioned this...!!!!

Synaptic has  bunch of mouse cursors you can install really easily

System>Admin>Synaptic

type in mouse in the search field, and you should get some options to install..

same thing for themes and icons


your welcome

---

