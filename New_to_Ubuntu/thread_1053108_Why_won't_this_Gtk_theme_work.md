---
title: "Why won't this Gtk theme work?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Gotaro on 2009-01-28
I'm trying to use the VistaBut Gtk 2.x theme, screenshots [at gnome-theme.org](http://gnome-look.org/content/show.php/VistaBut?content=32227), downloaded from the last post [here](http://www.neowin.net/forum/index.php?showtopic=441892) (note: remove .txt extension after downloading).

I extract the folder, move it to the themes folder @ /usr/share/themes/, in exactly the same format as the other themes.  It then shows up in my themes list (System Settings->Appearance->GTK Styles and Fonts), but when I select it, instead of replacing everything with the cool images, the menus are just a plain style, seemingly default (see screenshot).  I've tried relogging and restarting, but neither have any effect.

Am I doing something wrong?  Is the theme just broken?  This is sort of high priority for me :(.  (I gave up on it a few days ago in hopes that KDE 4.2 would provide me with an attractive alternative, which it didn't..)

--Edit--
Also, I have installed other themes successfully using this same method.

---

### Post by Gotaro on 2009-01-28
Searching the forums (and google, for that matter), I find only OLD posts, and ones that apply to Gnome.  There is an SS in the 2009 desktop pictures thread, but what he is calling the "VistaBut" theme is a window decoration, not a Gtk theme.

Is there a difference between KDE and Gnome Gtk themes?  I got this from **gnome**-look.org, but I just assumed a Gtk theme was a Gtk theme.  (I couldn't find anything remotely equivalent on kde-look.)

Thanks in advance for any responses!

---

### Post by Gotaro on 2009-01-28
Sorry to keep bumping, but I don't really know if the once/24 hours bump "in general" rule applies to a forum as busy as Absolute Beginner Talk.  This is kind of high priority for me..  It's really hard to justify using an outdated-looking OS over a pretty, modern-looking Windows 7.  It's even harder to justify upgrading components for it!  But that's another story..  Main point: if I can't get it to look decent, and won't use it long-term because of that, why take the time and patience to learn **how** to use it?

I have the taskbar look I want..  It could be improved, but it's very acceptable as-is.  The window decoration..  needs work..  and the Gtk theme is even worse.  But if I can get VistaBut to work, that'll be a huge step!

---

### Post by Gotaro on 2009-01-28
Can this thread be moved to the "Desktop Effects & Customization" forum, please?  Or should I just create a new thread?

---

### Post by bruce89 on 2009-01-28
> **Gotaro said:**
> Is there a difference between KDE and Gnome Gtk themes?  I got this from **gnome**-look.org, but I just assumed a Gtk theme was a Gtk theme.  (I couldn't find anything remotely equivalent on kde-look.)

KDE and GNOME themes are different, yes.

> **Gotaro said:**
> Sorry to keep bumping, but I don't really know if the once/24 hours bump "in general" rule applies to a forum as busy as Absolute Beginner Talk.  This is kind of high priority for me..  It's really hard to justify using an outdated-looking OS over a pretty, modern-looking Windows 7.  It's even harder to justify upgrading components for it!  But that's another story..  Main point: if I can't get it to look decent, and won't use it long-term because of that, why take the time and patience to learn **how** to use it?

It seems rather odd that you'd not be prepared to use a OS because its theme doesn't look like Windows. I suppose I'll never understand people wanting to use Windows-like themes.

Anyway, I can get this theme to install under GNOME.

---

### Post by Gotaro on 2009-01-28
> **bruce89 said:**
> KDE and GNOME themes are different, yes.



It seems rather odd that you'd not be prepared to use a OS because its theme doesn't look like Windows. I suppose I'll never understand people wanting to use Windows-like themes.

Anyway, I can get this theme to install under GNOME.
Thanks for the info!  It's not that I want it to look like Windows, but nothing is on par with the look of smoked glass, IMO.  (Cartoony themes are in the past! :P)  This theme has that smooth gradient effect that helps make everything look polished and modern.  Maybe I'll give Gnome a shot..

---

### Post by bruce89 on 2009-01-28
> **Gotaro said:**
> Maybe I'll give Gnome a shot..

You may be able to get the theme to work if you install *gnome-control-center* (sic). It would be a wee bit extreme to switch DE just for a theme. Mind you, all the KDE programs will use their default theme.

---

### Post by Gotaro on 2009-01-28
> **bruce89 said:**
> You may be able to get the theme to work if you install *gnome-control-center* (sic). It would be a wee bit extreme to switch DE just for a theme. Mind you, all the KDE programs will use their default theme.
Someone else suggested this, as well.  I'll go ahead and do it..  But from the looks, it installs the whole Gnome DE anyway.  Seriously, there are a LOT of packages bundled with it.

--Edit--
Yep, it installed Gnome lol.  But it was for the better..  now I understand that even Gnome window decorations are themed with the Gtk them!  I'm also surprised how much incredibly **faster** Gnome is..  Apps open and appear instantly.  I wonder why KDE is so slow?..

---

### Post by Gotaro on 2009-02-02
Wow..  Coming back to this thread again.  I was just going down the list of Gtk themes, applying each one and checking it out in FF, and got to the bottom of the list, decided to just see what VistaBut did again.  It works!  The images all load correctly, though the font is black when I think it should be white (on the toolbar).  However, restarting breaks it again.  After it breaks, I can't just re-apply it.  I went through and applied all 9 themes again, and sure enough, it works again!

Any thoughts on maybe getting it to work permanently?  Could I run a script at startup that goes through the list, applying each theme?

---

### Post by Dies on 2009-02-03
> **Gotaro said:**
> 
Any thoughts on maybe getting it to work permanently?  Could I run a script at startup that goes through the list, applying each theme?

It should stick, not sure why it's not for you, but you can try checking your home folder for a .gtkrc-2.0. Open Nautilus, hit control+h to show hidden files and see if you have that file if you do delete it, log out and back in then try again, if not you can try making the file and adding the path to the theme you want i.e.
```

include /home/$USER/.theme/vistabut/gtkrc/gtkrc-2.0
```

---

