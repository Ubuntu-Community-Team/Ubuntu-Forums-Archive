---
title: "****Murrine SVN Only****  What?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-25
So I was looking around at themes, and I came across this:

[http://www.gnome-look.org/content/show.php/Human-Reprise?content=98045](http://www.gnome-look.org/content/show.php/Human-Reprise?content=98045)

and it says on the page: ****Murrine SVN Only****


When I go to install and use the theme, it doesn't look anything like that.

I'm guessing I need Murrine SVN, but how do I get this?

I tried going to the murrine site but I still don't get how to get Murrine SVN or what it is.

Help would be appreciated.

---

### Post by lvlo on 2009-03-25
You can get it here: [https://launchpad.net/~suraia/+archive/ppa](https://launchpad.net/~suraia/+archive/ppa)

---

### Post by Gp. on 2009-03-25
Where?
I don't see anything about SVN on that page.

and if I need gtk2-engines-murrine

well it's already installed acording to Synaptic Package Manager

---

### Post by lvlo on 2009-03-25
You need to install this package: [https://launchpad.net/%7Esuraia/+archive/ppa/+files/gtk2-engines-murrine_0.90.2-0ubuntu1~intrepid1_i386.deb](https://launchpad.net/%7Esuraia/+archive/ppa/+files/gtk2-engines-murrine_0.90.2-0ubuntu1~intrepid1_i386.deb)

It's the latest version Murrine GTK engine - 0.90.2. If you use Intrepid, you have version 0.60.1. SVN = SubVersioN.

:)

---

### Post by Gp. on 2009-03-25
Well I installed that, and it still won't display properly.

This is the theme: [http://www.gnome-look.org/content/show.php/Human-Reprise?content=98045](http://www.gnome-look.org/content/show.php/Human-Reprise?content=98045)


Don't know why I can't get it to display properly

---

### Post by lvlo on 2009-03-25
It works for me, but I'm using Jaunty...

---

### Post by mister_pink on 2009-03-25
svn is subversion, a program for keeping track of changes made to source files. When someone says you need "whatever SVN" it just means you need the latest version. Add the ppa as recommended and it will upgrade the version you already have installed to the one in the ppa, which is presumably new enough.

---

### Post by Gp. on 2009-03-25
I have already updated it to the latest...

this is what the human-reprise theme looks like when I use it...

---

### Post by Therion on 2009-03-25
That looks right to me (your screenshot), but I'm on my first cup of coffee.  Are you thinking the windows should be decorated with blue instead of the typical "Human Orange"?  Because they're not... It's still the original "Human" theme, just tweaked a bit with some darker color and some other subtle changes.

---

### Post by Gp. on 2009-03-25
[http://www.gnome-look.org/content/sh...?content=98045](http://www.gnome-look.org/content/sh...?content=98045)

That is definitely very different to my sreenshot.

The menus from the panel bar are translucent, there are rounded edges on the menus and the panel is a different look altogether to mine.


Mine are not translucent and do not look like that?

---

### Post by Therion on 2009-03-25
> **Gp. said:**
> [http://www.gnome-look.org/content/sh...?content=98045](http://www.gnome-look.org/content/sh...?content=98045)

That is definitely very different to my sreenshot.
Your link 404's on me.

In looking at the theme though, and your screenshot, I can tell you that the differences you see are not JUST from the theme in question.

The transparency is being done, most likely, by Compiz for instance.  The theme is JUST the GTK elements.

As for the Panel, that is addressed in the comments section on Gnome-Look:

> How I can have the top panel like in the screen shot? Im using the theme and everything looks like the screen shot except the top panel.

> ... [qubzr branch lp:~dashua/murrine-themes/Murrine-Testing

Pull the source from bzr. I uploaded the panel_bg and a few other changes along with some extra themes I'm working on.

---

### Post by Gp. on 2009-03-25
Oh,

Do you know where to set the transparency in Compiz?

And what about the way the menus look? They are rounded whereas mine are just straight rectangles

---

