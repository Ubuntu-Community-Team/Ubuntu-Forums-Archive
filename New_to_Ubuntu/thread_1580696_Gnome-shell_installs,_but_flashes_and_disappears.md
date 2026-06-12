---
title: "Gnome-shell installs, but flashes and disappears?"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by iu34 on 2010-09-23
So, I _finally_ fix the dependency conflict between libgjs0 and xulrunner, and gnome-shell finally installed through ppa:ricotz/testing. But now, when I run gnome-shell --replace in a terminal, I get this.

```
(mutter:12008): mutter-WARNING **: Plugin API mismatch for [/usr/lib/mutter/plugins/libgnome-shell.so]
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```

Gnome shell still doesn't work after all. It only flashes and disables compiz until I run compiz --replace.

Can  someone help? All I want to do is get gnome-shell installed. It worked perfectly in 9.10. WHY IS IT SO HARD IN 10.04?!

---

### Post by Jesus_Valdez on 2010-09-23
The ricotz ppa has been unusable for weeks now. 

I recommend install the one that comes withg the official repos.

---

### Post by jtarin on 2010-09-23
Where did you download from and what documents have your referred to to make the installation?

---

### Post by iu34 on 2010-09-23
okay, so I removed the ricotz/testing from my sources, ran a sudo apt-get update, uninstalled gnome-shell, then tried reinstalling through the ubuntu software center and got this error message.
> This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.
the "details" dropdown menu just says "gnome-shell". Nothing more, nothing less. So how do I know what's missing or whatever?

---

### Post by Jesus_Valdez on 2010-09-23
Check from Synaptic if everything is properly removed.

Also, a sudo apt-get autoremove  don't hurt.

---

### Post by iu34 on 2010-09-23
Well, so much for the conflict being fixed. I guess somewhere in the past hour or so it unfixed itself. 

So now, it's still complaining about libgjs0, which in turn complains about xulrunner being the wrong version. Can't someone help me get this fixed once and for all?

---

### Post by jtarin on 2010-09-23
Go on IRC where there are people that are involved in the development.

> IRC: Join irc.gnome.org:#gnome-shell to participate in daily discussions or get help with running, developing, or designing for the GNOME Shell.

[More info and links.]("http://live.gnome.org/GnomeShell#Running")

---

### Post by iu34 on 2010-09-23
I've never messed with IRC before,and just installed x-chat...so I'm really lost on how to get to that channel you mentioned. :confused: I'm a retard :P

---

### Post by jtarin on 2010-09-23
[Here ya go!]("https://help.ubuntu.com/community/XChatHowto")

---

