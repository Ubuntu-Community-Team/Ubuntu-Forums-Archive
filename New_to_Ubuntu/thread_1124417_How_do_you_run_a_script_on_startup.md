---
title: "How do you run a script on startup?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by HeLzWright on 2009-04-13
"How do you run a script on start up"

I've been trying to figure this out just because I am lazy. 

I want to restart some desklets to get them off of my bottom toolbar

start up my torrent prog

and a few other things but I do not know how to do this and I do know that I could severely mess things up if I do not know what I'm doing.

Soooooooooooooo.... any help would be AWESOME!

---

### Post by Hospadar on 2009-04-13
well in gnome, you can add startup commands in System->Preferences->Startup Applications (or maybe it's called sessions?)

These will run as soon as you log in.
So let's say you have a script you want to run saved in ~/scripts/yourscript.sh (~ is short for your home director if you didn't know), then you might add "bash ~/scripts/yourscript.sh"  or "sh ~/scripts/yourscript.sh"

For regular programs, just add them directly, let's say I want transmission bittorrent to start up when I log in, just add "transmission" (as the command) to this area.

There are other ways to make programs run on bootup if you don't have a graphical environment, or you have some backend tool you want to startup even before gnome starts, but that's more of a pain, and for everyday things on a desktop machine this is a much better way to do things.

---

