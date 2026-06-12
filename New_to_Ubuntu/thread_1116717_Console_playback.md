---
title: "Console playback"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by NaF on 2009-04-05
I don't know whether it's my wording that's a bit off, but I haven't been able to dig anyone up on Google.
Is it possible to dedicate one of the alt f[1-6]-logins to an application.
Say I want alt f6 to be play music via mpg123, at startup - is this possible?

---

### Post by freak42 on 2009-04-05
> Is it possible to dedicate one of the alt f[1-6]-logins to an application.
sure
> Say I want alt f6 to be play music via mpg123, at startup - is this possible?
I'm sure you can also start a console audio player.. but do you mean like auto-start/auto-login?.. not sure.. googling "tty auto login" or "tty auto start" might be worth a try.

---

### Post by fooman on 2009-04-05
not sure what your looking for....but you can assign key-combinations in system > preferences > keyboard shortcuts

to open a media player with the alt-f6 combo...just click once on "launch media player".  then press the alt & f6 keys to set them.  close the keyboard shortcuts box.

open up "preferred applications" (system > preferences > preferred applications) and click the "multimedia" tab.  choose a player to set as default from the drop-down menu (or choose "custom" and type the name of the app you want in the space provided).  then close that box and press alt-f6 to see if it works,

hope that helps.

---

### Post by NaF on 2009-04-05
> **freak42 said:**
> do you mean like auto-start/auto-login?.. not sure.. googling "tty auto login" or "tty auto start" might be worth a try.

Yes that's exactly what I mean, but there's no help to find on mother google :/

---

### Post by NaF on 2009-04-05
> **fooman said:**
> not sure what your looking for....but you can assign key-combinations in system > preferences > keyboard shortcuts

to open a media player with the alt-f6 combo...just click once on "launch media player".  then press the alt & f6 keys to set them.  close the keyboard shortcuts box.

open up "preferred applications" (system > preferences > preferred applications) and click the "multimedia" tab.  choose a player to set as default from the drop-down menu (or choose "custom" and type the name of the app you want in the space provided).  then close that box and press alt-f6 to see if it works,

hope that helps.

That's not quite what I was looking for; I'm one of the fortunate to have discovered gnome-do :D. I'm looking for a way to auto-login into one of the tty-login's assigned to alt-f[1-6] and start up the text-based mediaplayer mpg123

---

### Post by krzysz00 on 2009-04-05
ok. let me get this straight. You want one of the tty playing an audio file on system startup. If so try editing/creating the inittab (I'll post one later). NOTE: _this will prevent you from using said tty for logins_

---

### Post by NaF on 2009-04-05
> **krzysz00 said:**
> ok. let me get this straight. You want one of the tty playing an audio file on system startup. If so try editing/creating the inittab (I'll post one later). NOTE: _this will prevent you from using said tty for logins_

My whole playlist rather, but yes - that's the plan :)

---

### Post by sisco311 on 2009-04-05
> **NaF said:**
> My whole playlist rather, but yes - that's the plan :)

never tried myself, but i think you can use rungetty:
```
sudo aptitude install rungetty
```

and edit the /etc/event.d/tty6 file to:
```
respawn
exec /sbin/rungetty tty6 --autologin username -- /path/to/command args
```

---

### Post by NaF on 2009-04-05
> **sisco311 said:**
> 
```
sudo aptitude install rungetty
```

and edit the /etc/event.d/tty6 file to:
```
respawn
exec /sbin/rungetty tty6 --autologin username -- /path/to/command args
```

Not sure if I'm doing it right - but tty6 is just a "_" blinking, after I installed rungetty and wrote the following to /etc/event.d/tty6:

```
#respawn
#exec /sbin/getty 38400 tty6
respawn
exec /sbin/rungetty tty6 --autologin naf -- mpg123 -v -Z -@ /home/naf/playlist.lst
```

---

### Post by sisco311 on 2009-04-05
after reading the man page, think:
```
respawn
exec /sbin/rungetty tty6 -u naf -- mpg123 -v -Z -@ /home/naf/playlist.lst
```should work.

also use the full path to the command(/usr/bin/mp123?).

---

### Post by NaF on 2009-04-05
> **sisco311 said:**
> after reading the man page, think:
```
respawn
exec /sbin/rungetty tty6 -u naf -- mpg123 -v -Z -@ /home/naf/playlist.lst
```should work.

also use the full path to the command(/usr/bin/mp123?).

Hm, I need some help to be quite honest. I've trying to fiddle with this for a couple of hours and gone nowhere. 
No matter how I try and call rungetty on tty6, it just remains there with an unresponsive  "_"-blinker. 

When I don't add any -[options], it actually gets me the login-screen, as it would've done without running rungetty in the first place. But whenever I add ```
-u naf
``` or ```
--autologin naf
``` it just sits there blinking.
I don't know, whether I should specify a group for the user naf also?  (I don't know which group that would be in, anyways) or what I'm doing wrong. 
```
apt-get install rungetty
``` says it's the current version and no updates available, so I guess it's installed correctly.

Any help would be appreciated :)

---

### Post by NaF on 2009-04-06
bumb

---

