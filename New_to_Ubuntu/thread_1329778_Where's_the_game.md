---
title: "Where's the game?"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by maxximilian on 2009-11-17
Hiya

I just installed a game called The racer. Install seemed to go smooth.....but I don't see how to start the game. No icons or listings in menues. How do I start it?

---

### Post by NickJones on 2009-11-17
Hmm, where did you install it from?

---

### Post by dillandriskell on 2009-11-17
I just lost the game when I saw that title :(

But I've noticed that sometimes games either don't show up immediately after install (which simply means you have to log out and log back in) or don't ever show up in the menu.  So I'd try logging out then logging back in, if it's in the games section then great.

If not you can probably start it from a terminal, just open a terminal (**Applications > Accessories > Terminal**) and type the name of the game, I'd try just typing **racer** and seeing if that works.

---

### Post by maxximilian on 2009-11-17
I installed from the dektop with a .run file....

As the installer ran, I saw a glimpse of something saying adding to menues. I will try a restart.....

Thanks...

---

### Post by maxximilian on 2009-11-17
Restart didn't do it. Typing "racer" into the terminal returned a no command found error. The game did install. I can see it /home/**me**/racer

Just can't seem to figure how to run it.....

---

### Post by NickJones on 2009-11-17
Hmmm, where did you get the game from? It may be possible to get it from Symtamatic - that will install all of the short cuts and annoying stuff for you,

---

### Post by maxximilian on 2009-11-17
I was reading at the homesite for the game development and there was a link to a place where they said there was an installer I could use (easier for noobs). Forget exactly what it was....but Loki-something or another....

---

### Post by maxximilian on 2009-11-17
Found the site...

Here is where I got the installer from.... [http://www.liflg.org/?catid=6](http://www.liflg.org/?catid=6)

---

### Post by redseventyseven on 2009-11-17
as a temporary solution (before we try to get the game into the menus):

are there any binary (linux equivalent of "executable") files in the directory you found?

try navigating to the directory:
```
cd ~/racer
```
(the "~" character is a shorthand way of typing your "/home/***me***" directory)

and try to run the program using:
```
./racer
```
(the "." character is a shorthand way of typing "this directory" - when you run programs, unlike DOS, linux doesn't look in the current directory unless you specifically ask it to)

Give that a try!

---

### Post by maxximilian on 2009-11-17
OK....those commands worked. I have a splash screen for the game up now. :)

So can I assume the game is fine, I am just missing the easy way to run it?

---

### Post by NickJones on 2009-11-17
And that easier way is by creating a launcher. Right click on a blank part of your desktop, and select Create Launcher!

---

### Post by maxximilian on 2009-11-17
Game works.... :)

I did three laps of free drive. I suck....but the game works. Thanks. :)

---

### Post by redseventyseven on 2009-11-17
...and the command you'll need to set for the launcher will be:
```
~/racer/racer
```

---

### Post by maxximilian on 2009-11-17
> **NickJones said:**
> And that easier way is by creating a launcher. Right click on a blank part of your desktop, and select Create Launcher!

Do I use the same terminal command when configuring the launcher?

---

### Post by maxximilian on 2009-11-17
Whoops...you already answered my question. Thanks again. :)

---

