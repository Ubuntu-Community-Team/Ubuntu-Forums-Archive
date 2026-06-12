---
title: "Removing gnome-shell"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by susanpenter on 2010-04-03
Following issue 129 of Linux Format I installed gnome-shell and found a post which told me how to set it up so that this installed instead of the usual gnome system. However since I have done this I have had many problems and would like to go back to the traditional Gnome face, does anyone know how I can do this.

Thanks,

Susan

---

### Post by NCLI on 2010-04-03
We'll need to know what you have changed. Please post a detailed overview of how you did it.

---

### Post by susanpenter on 2010-04-11
Doing a websearch I think I did this:

From standard Gnome, open System > Preferences > Startup apps (or session apps), and add an entry for Gnome-Shell running
Code:
gnome-shell --replace

---

### Post by susanpenter on 2010-04-24
I guess there is no way to reverse this then, usually on this forum someone comes up with an idea very quickly but it has been a week now.

---

### Post by wojox on 2010-04-24
> **susanpenter said:**
> Doing a websearch I think I did this:

From standard Gnome, open System > Preferences > Startup apps (or session apps), and add an entry for Gnome-Shell running
Code:
gnome-shell --replace

So I take it you deleted that start up file and it still boots to gnome-shell?

---

### Post by kh1116 on 2010-04-24
try typing in "metacity --replace" in a terminal

---

### Post by susanpenter on 2010-04-24
I tried this Kh1116 and now I have no gnome-shell and have not got the original back in it's place just a blank wallpaper with a couple of icons no tool bars or anything, I'm far worse of that ever

---

### Post by Silent Warrior on 2010-04-24
See if hitting Alt+F2 (popping up a Run-prompt) and entering 'gnome-panel' helps you any.

I see there's also a command called gnome-session - I don't know what exactly it does (from its man-page it LOOKS like it just starts the Gnome desktop, i.e. what happens after log-in). Anyone care to shed some light on that?

---

### Post by susanpenter on 2010-04-24
To counteract this as I still had the terminal open I redid the gnome shell replace again. It is better than nothing.

---

### Post by wojox on 2010-04-24
Unset it:

```
gconftool-2 -unset /desktop/gnome/session/required_components/windowmanager
```

---

### Post by susanpenter on 2010-04-24
> **wojox said:**
> Unset it:

```
gconftool-2 -unset /desktop/gnome/session/required_components/windowmanager
```

I tried this and got this reply

```
Error while parsing options: Unknown option -unset.
Run 'gconftool-2 --help' to see a full list of available command line options.
susan@susan-desktop:~$ gconftool-2 --help
```

---

### Post by wojox on 2010-04-25
> **susanpenter said:**
> I tried this and got this reply

```
Error while parsing options: Unknown option -unset.
Run 'gconftool-2 --help' to see a full list of available command line options.
susan@susan-desktop:~$ gconftool-2 --help
```

Sorry I forgot a hyphen.

```
gconftool-2 --unset /desktop/gnome/session/required_components/windowmanager
```

---

### Post by Calash on 2010-04-25
> **susanpenter said:**
> Doing a websearch I think I did this:

From standard Gnome, open System > Preferences > Startup apps (or session apps), and add an entry for Gnome-Shell running
Code:
gnome-shell --replace

You should be able to go to startup apps and remove the entry you added


From Gnome shell click on Activities, the type Startup and select Startup Applications.  Uncheck the entry you added for Gnome Shell (Name will depend on what you typed when you first followed the tutorial).  Press Close and then restart the system.

---

### Post by rodi.rock on 2010-10-14
Try to run this ...

gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "compiz" -t string

then logout or restart ubuntu

it worked for me

enjoy

---

