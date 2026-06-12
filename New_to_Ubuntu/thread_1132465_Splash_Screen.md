---
title: "Splash Screen"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by shynthriir on 2009-04-21
I've been playing around trying to change the splash screen, which I believe (and hoping I'm right) is the ubuntu loading screen with the orange bar that progresses while you boot the system. I did some tinkering anf now I don't have a splash screen at all. Right now I just want to set everything back to default. The two things I have been messing with are the configuration editor in the system tools (apps --> gnome-session ->  options) and startupmanager, I've checked and/or unchecked buttons in Boot Options and Appearance tabs and tried changing the usplash theme, I added one usplash theme (.so file) but then removed it in attempts to reset everything.

Anyway, like I said, my main goal atm is just to get it all back to normal if possible, default if you will. If you can include instructions on changing the splash screen, that would be big kudos to you too!

Currently running Ubuntu 8.10 Intrepid Ibex with Gnome 2.24.1 (which is what Intrepid installs with)
Gateway ML3109 upgraded to 1.5G RAM in case it matters

---

### Post by mprince on 2009-04-21
This will reinstall usplash with default settings:

```

sudo apt-get install usplash
```

---

### Post by hyperyoda on 2009-04-21
> **shynthriir said:**
> I've been playing around trying to change the splash screen, which I believe (and hoping I'm right) is the ubuntu loading screen with the orange bar that progresses while you boot the system. I did some tinkering anf now I don't have a splash screen at all. Right now I just want to set everything back to default. The two things I have been messing with are the configuration editor in the system tools (apps --> gnome-session ->  options) and startupmanager, I've checked and/or unchecked buttons in Boot Options and Appearance tabs and tried changing the usplash theme, I added one usplash theme (.so file) but then removed it in attempts to reset everything.

Anyway, like I said, my main goal atm is just to get it all back to normal if possible, default if you will. If you can include instructions on changing the splash screen, that would be big kudos to you too!

Currently running Ubuntu 8.10 Intrepid Ibex with Gnome 2.24.1 (which is what Intrepid installs with)
Gateway ML3109 upgraded to 1.5G RAM in case it matters


Hi!

Here is an app that will let you switch it:
[http://www.gnomefiles.org/app.php/gnome-splash-screen-switcher](http://www.gnomefiles.org/app.php/gnome-splash-screen-switcher)

If you don't have any themes you may like some of these:
[http://www.gnome-look.org/content/show.php/Elegant+Splash+Screen+(GNOME)?content=76917](http://www.gnome-look.org/content/show.php/Elegant+Splash+Screen+(GNOME)?content=76917)

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

This embeds a gnome lession inside a window so you don't have to keep logging off and on to test your different spash screens.

Enjoy!

---

### Post by shynthriir on 2009-04-22
Okay, quick question, in that procedure given, does the image have to be in .png format or can it be a different image type? What image types are supported?

Note: I attempted to follow those steps with a .jpg image because I did not have a .png image handy, and it did not work.

---

### Post by philinux on 2009-04-22
Use gimp then save as and use png as the extension.

---

### Post by shynthriir on 2009-04-22
I know to save as a png, my question was MUST it be a png image?

I would test it now if I was at my home computer.

---

### Post by Godly on 2009-04-22
> **hyperyoda said:**
> Hi!

Here is an app that will let you switch it:
[http://www.gnomefiles.org/app.php/gnome-splash-screen-switcher](http://www.gnomefiles.org/app.php/gnome-splash-screen-switcher)

If you don't have any themes you may like some of these:
[http://www.gnome-look.org/content/show.php/Elegant+Splash+Screen+(GNOME)?content=76917](http://www.gnome-look.org/content/show.php/Elegant+Splash+Screen+(GNOME)?content=76917)

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

This embeds a gnome lession inside a window so you don't have to keep logging off and on to test your different spash screens.

Enjoy!

VERY good post! 
+1 for you.

---

