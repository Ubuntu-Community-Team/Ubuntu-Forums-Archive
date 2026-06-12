---
title: "Disable Alt-Key Menu Access Functionality"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by andymandias on 2011-04-21
I've recently made the switch over to Ubuntu, and have been enjoying the change by and large.  These forums have been a great resource while configuring and tweaking Ubuntu, but it seems I've finally come up with a change I want to make that I can't find by searching here.

My goal is to disable the part of the functionality of the Alt key that I never use. Specifically the ability to open window menus using Alt-<Menu's First Letter>.  I do NOT, for example, want to be able to open the File menu by typing Alt-F.

I want to disable this functionality so I can use those key combinations as shortcuts within applications.  I like to use the Emacs gtk_key_theme for its text navigation key bindings, but those key bindings interfere with some of the default shortcuts (e.g. Ctrl-A is often bound to Select All).  I decided I would try to switch the modifying key of the default shortcuts over to Alt.  (Super/Win is also an option, but not a serious one until I find a way to disable shortcuts like Super-A which enables a cross-workspace window chooser.)

I've changed as much as I can using application preferences, but keyboard shortcut configuration doesn't seem like a popular feature.  So, I've enabled can_change_accels such that I can hover the mouse pointer over a menu item and change its shortcut by typing my own.  For the most part this works great, but there are times that the shortcut refuses to change to the one I'm typing.  The only reason I can see that the shortcuts are not changing in these cases is because they are being used; often the only use I can ascertain is as window menu access shortcuts (e.g. Alt-V in gedit brings up the View menu when I would like it to paste).

Is there any way I can disable this functionality?  I realize that there could be some strange series of events that could make general window menu access through the keyboard useful to me again, but it seems unlikely enough I'd like to risk it.

---

### Post by andymandias on 2011-04-29
I was hoping the upgrade to Natty Narwhal might offer some new functionality (that I can find), but it seems that Unity has made this problem worse.  I cannot find a way to edit menu shortcuts in applications that do not have preferences for them (previously was using can_change_accels).  The changes I had made before are now locked in place it seems.

Am I crazy in thinking of this as a fundamental feature of the OS?

---

### Post by andymandias on 2011-05-05
An update!

The can_change_accels problem I mentioned is apparently a bug ([https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/610234](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/610234)) and since I currently have neither the time nor expertise to fix it myself I will simply have to live with it.

It seems, however, that I have stumbled upon a possible solution to my alt-key menu access functionality problem (alt-key mnemonics access functionality).  Apparently there is a setting in GTK to control this ([http://developer.gnome.org/gtk/stable/GtkSettings.html#GtkSettings--gtk-enable-mnemonics](http://developer.gnome.org/gtk/stable/GtkSettings.html#GtkSettings--gtk-enable-mnemonics)).  However, when I open up gconf-editor I cannot find this key (only the terminal-specific preference shows up when I search for 'mnemonic').  Please, how can I change this setting properly?

---

### Post by andymandias on 2011-05-13
Well, I figured it out.

To disable mnemonics you should create (if it doesn't already exist) **~/.gtkrc-2.0**. This file should contain the line **gtk-enable-mnemonics = 0** (you can add other [GTK settings]("http://developer.gnome.org/gtk/stable/GtkSettings.html") if you'd like).  Then, restart for the changes to take effect (you may be able to log out then log in instead).

The alt key will still make menus appear in some cases, but the mnemonics are now disabled.   Hoorah!

---

