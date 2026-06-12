---
title: "Problem Installing Splash Screen"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-04-23
I am running Ubuntu 8.10. Following is a copy of a previous post and reply of how to set up a new splash screen. I decided to follow the manual procedure outlined but when I got to the testing of the splash screen I received the message."Cannot Start New Display. You do not seem to have the authentication needed for this operation. Perhaps your.Xauthority file is not set up correctly."

On reboot of the system (I have a dual boot setup) the splash screen was the usual light tan.

How do I resolve the problem? I have no idea what the authority issue is all about.

Quote:
Originally Posted by shynthriir 
I've been playing around trying to change the splash screen, which I believe (and hoping I'm right) is the ubuntu loading screen with the orange bar that progresses while you boot the system. I did some tinkering anf now I don't have a splash screen at all. Right now I just want to set everything back to default. The two things I have been messing with are the configuration editor in the system tools (apps --> gnome-session -> options) and startupmanager, I've checked and/or unchecked buttons in Boot Options and Appearance tabs and tried changing the usplash theme, I added one usplash theme (.so file) but then removed it in attempts to reset everything.

Anyway, like I said, my main goal atm is just to get it all back to normal if possible, default if you will. If you can include instructions on changing the splash screen, that would be big kudos to you too!

Currently running Ubuntu 8.10 Intrepid Ibex with Gnome 2.24.1 (which is what Intrepid installs with)
Gateway ML3109 upgraded to 1.5G RAM in case it matters

Hi!

[B]Here is an app that will let you switch it:
[http://www.gnomefiles.org/app.php/gn...creen-switcher](http://www.gnomefiles.org/app.php/gn...creen-switcher)

If you don't have any themes you may like some of these:
[http://www.gnome-look.org/content/sh...?content=76917](http://www.gnome-look.org/content/sh...?content=76917)

Or to do it manually:

Create an image file, such as mysplash.png, then do:

$ sudo cp mysplash.png /usr/share/pixmaps/splash/. 

Then do:

$ sudo gconf-editor. This launches the Gnome Configuration Editor.

Go to: Apps -> Gnome-Session -> Options

Replace <splash_image> with mysplash.png and you're all set.

BTW you can test it out without logging off and back in if you do:

$ sudo apt-get install xnest

After it installs run:

$ sudo gdmflexiserver --xnest

This embeds a gnome lession inside a window so you don't have to keep logging off and on to test your different spash screens.[/B]

---

### Post by camnor on 2009-04-25
Hey!
Was this run with the sudo command included?  You should have been able to change your splash screen no problem because sudo makes you root temporarily.  In an off hand sort of way however.  Also, was the splash scrren called mysplash.png?

---

