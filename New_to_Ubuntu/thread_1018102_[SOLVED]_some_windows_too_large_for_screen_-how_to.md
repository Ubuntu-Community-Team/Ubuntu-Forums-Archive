---
title: "[SOLVED] some windows too large for screen -how to resize?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Amanda HazLaPaz on 2008-12-21
[IMG]http://img.photobucket.com/albums/v324/Manderpants/Screenshot-falconseye.png[/IMG]

This is a screenshot of Falcon's Eye. I cannot access the information along the bottom, and as you can see, there are only two options at top right: minimize and close. I can move the task bar at bottom off to the side and that helps a little, but not enough. Obviously I've already tried to move the sides, but I just scroll over within the game-- the window size stays static.

The "too large" effect happens with some other apps, too.

Any suggestions about how to make a window conform to the space allotted?

Thanks--

---

### Post by IamReck on 2008-12-21
You may want to try auto hidiing that bottom panel, or taking the window you are using out of Maximum mode, and resizing it yourself.

What other apps does it happen for, because the problem you are having with Falcon's Eye might be specific to that application.

---

### Post by Tatty on 2008-12-21
As this is a game, its probable that the size of the window is fixed by the game itself.  See if there is an option in the game to reduce the screen resolution.

---

### Post by jimmy the saint on 2008-12-21
If it happenes with standard windows (ie not full screen mode) you can hold down the ALT key and click anywhere in the window to drag the window around and expose the lower right resize section.

---

### Post by Amanda HazLaPaz on 2008-12-21
> **IamReck said:**
> You may want to try auto hidiing that bottom panel, or taking the window you are using out of Maximum mode, and resizing it yourself.

Thank you, I did move the panels out of the way as you suggested. There appears to be no way to resize it: when I take it out of Maximum mode, it zooms to the task bar-- no options.

> What other apps does it happen for, because the problem you are having with Falcon's Eye might be specific to that application.



It happened just now when uploading the image to photobucket-- the chooser "where do ya wanna upload the image from" window is way long, and I have to grab the title bar and yank it over to the left to get to the "cancel/ok" options on the right. The file option seems to be the problem: photobucket lists all compatible types and it's on a single line instead of wrapping.

I've seen it happen in some audio stuff, too, but nothing I can say specifically. Sorry.

---

### Post by Amanda HazLaPaz on 2008-12-21
> **Tatty said:**
> As this is a game, its probable that the size of the window is fixed by the game itself.  See if there is an option in the game to reduce the screen resolution.

No, unfortunately, there was none. Could I manually reset the screen resolution before starting the game?

---

### Post by Amanda HazLaPaz on 2008-12-21
> **jimmy the saint said:**
> If it happenes with standard windows (ie not full screen mode) you can hold down the ALT key and click anywhere in the window to drag the window around and expose the lower right resize section.

Oddly, it still won't resize even with the cursor at the lower right. 

I'm marking this thread as solved, though, because your suggestion of hitting ALT and dragging the window around was the fix I needed. I moved the task and menu bars to the side and dragged the window title bar up and out of site. That gives me enough room to see the other options.  Thanks very much for sharing that with me!

---

### Post by Tatty on 2008-12-21
I found this : [http://www.linuxjournal.com/article/8491](http://www.linuxjournal.com/article/8491)

> Falcon's Eye starts in full-screen mode by default, which although cool, isn't what I want when I'm pretending to work while slaying goblins. To change the screen resolution to windowed mode, you need to edit the game's configuration file. It is called jtp_opts.txt, and you'll find it in the game's config directory. Here's the section you are looking for:

screen_xsize=800
screen_ysize=600
fullscreen=0


All you need to do then is edit jtp_opts.txt to bump your screen resolution down, alternatively you could set it to run fullscreen rather than windowed.

---

### Post by Amanda HazLaPaz on 2008-12-21
> **Tatty said:**
> I found this : [http://www.linuxjournal.com/article/8491](http://www.linuxjournal.com/article/8491)



All you need to do then is edit jtp_opts.txt to bump your screen resolution down, alternatively you could set it to run fullscreen rather than windowed.

Wow, thanks for going to all that trouble!!  That's awesome. Now to work up the nerve to muck around in a config directory... 

You're very kind to do all that searching.

---

### Post by Tatty on 2008-12-21
> **Amanda HazLaPaz said:**
> Wow, thanks for going to all that trouble!!  That's awesome. Now to work up the nerve to muck around in a config directory... 

You're very kind to do all that searching.

No problem, it was only a quick google search;)

If you are worried about altering a config file then simply back it up first, then if it goes wrong you can always go back to where you were.

A good standard way to backup the file is to make a copy of it and add .backup to the end, so just make a copy of the file called jtp_opts.txt.backup

---

