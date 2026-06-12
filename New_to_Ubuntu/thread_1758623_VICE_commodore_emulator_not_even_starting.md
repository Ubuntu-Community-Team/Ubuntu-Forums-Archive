---
title: "VICE commodore emulator not even starting"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by Spyro543 on 2011-05-14
I haven't posted for ever here, but I just got VICE Commodore emulators and here's the big problem - It won't even start! I have a desktop shortcut - I double clicked on it and nothing! Same thing for the menu item! I've already tried reinstalling it, what to do?

I'm running Ubuntu 10.10 on a Samsung N150 Plus

Sorry if this is in the wrong section, I'm not familiar with all of the sections of this forum.

---

### Post by Thewhistlingwind on 2011-05-14
> **Spyro543 said:**
> I haven't posted for ever here, but I just got VICE Commodore emulators and here's the big problem - It won't even start! I have a desktop shortcut - I double clicked on it and nothing! Same thing for the menu item! I've already tried reinstalling it, what to do?

I'm running Ubuntu 10.10 on a Samsung N150 Plus

Sorry if this is in the wrong section, I'm not familiar with all of the sections of this forum.

You need ROMS. See the documentation for details. Also, try running it from terminal under x64, will help bunches.

---

### Post by Spyro543 on 2011-05-14
So I can't even start the Commodore startup screen? :(

And what documentation??? :confused:

Oh yeah and I get this error at terminal:

C64MEM: Error - Couldn't load kernal ROM `kernal'.

---

### Post by Thewhistlingwind on 2011-05-14
> **Spyro543 said:**
> 

And what documentation??? :confused:

usr/share/doc/Vice

Yes, it doesn't list it anywhere, I spent an eternity finding it.

---

### Post by wep940 on 2011-05-14
> **Spyro543 said:**
> So I can't even start the Commodore startup screen? :(
 
And what documentation??? :confused:
 
Oh yeah and I get this error at terminal:
 
C64MEM: Error - Couldn't load kernal ROM `kernal'.
 
+1 For what Thewhistlingwind is telling your - notice it didn't find a ROM image to run?

---

### Post by Spyro543 on 2011-05-15
Yes, I see now. And there are ROMs of everything I want (startup screen, games, programs)?

WAIT - It won't let me copy any of the files to the folder I need to copy them to! It says permission denied.

---

### Post by wep940 on 2011-05-15
I'm not familiar with the actual package you are working with, so I don't know where it puts it's files.  However, if you are having permission problems try using "sudo".  This will temporarily super user rights so you should be able to copy the files.

---

