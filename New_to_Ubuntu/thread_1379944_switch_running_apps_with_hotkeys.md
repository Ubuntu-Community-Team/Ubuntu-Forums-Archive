---
title: "switch running apps with hotkeys"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by agroszer on 2010-01-13
Hi there,

I'm looking for a way to switch between running apps with configurable hotkeys.
E.g. shift+ctrl+alt+F switches to FireFox, shift+ctrl+alt+C switches to console, etc.
Any ideas how to do that with linux / ubuntu gnome?

---

### Post by darthmob on 2010-01-13
Sounds good! I would be interested in that as well.

What I'm currently doing is using different workspaces for different applications. Eg. Firefox runs always on the first workspace, im / mail on the second and so on. That makes it relatively easy to switch to the application I want.

---

### Post by lotharmat on 2010-01-13
> **darthmob said:**
> Sounds good! I would be interested in that as well.

What I'm currently doing is using different workspaces for different applications. Eg. Firefox runs always on the first workspace, im / mail on the second and so on. That makes it relatively easy to switch to the application I want.


How did you get Firefox to always run on the first workspace?

---

### Post by audiomick on 2010-01-13
there's also a whizz bang window swithcher thing in compiz. You might have to have all the desktop effects on.
the key combination is alt+tab

---

### Post by Sir Jasper on 2010-01-13
Hi,

If you make shortcuts (personally I use the Windows key for Programs - so say using, Win + F for Firefox and Win + C for your Console).

Now for example, if Firefox is not in use, Win + F should load it, but if
Firefox is ¨resting¨ on any Desktop Win + F should bring it into focus.

My regards

---

### Post by darthmob on 2010-01-13
> **lotharmat said:**
> How did you get Firefox to always run on the first workspace?It's the first thing I run when I start my computer and I don't move it. ;)

You can set up filters in [Openbox]("http://openbox.org/wiki/Help:Applications") though. It allows you to specify which application or group of applications starts on which workspace, if it should use window decorations or what size it is and all kinds of stuff. It's not perfect but a nice feature and I'm not sure if there are other window managers who can do that.

---

### Post by agroszer on 2010-01-13
> **Sir Jasper said:**
> Hi,

If you make shortcuts (personally I use the Windows key for Programs - so say using, Win + F for Firefox and Win + C for your Console).

Now for example, if Firefox is not in use, Win + F should load it, but if
Firefox is ¨resting¨ on any Desktop Win + F should bring it into focus.

My regards
That starts FireFox always, does give the focus to a running one. (If we speak of keyboard shortcuts)

---

### Post by DestructionsRightHand on 2010-01-13
System-Preferences-Keyboard Shortcuts for the basics

---

### Post by agroszer on 2010-01-14
This comes close to what I need:

[http://somanov.wordpress.com/2009/12/02/window-shortcuts-for-linux-desktops/](http://somanov.wordpress.com/2009/12/02/window-shortcuts-for-linux-desktops/)

---

### Post by darthmob on 2010-04-11
> **agroszer said:**
> This comes close to what I need:

[http://somanov.wordpress.com/2009/12/02/window-shortcuts-for-linux-desktops/](http://somanov.wordpress.com/2009/12/02/window-shortcuts-for-linux-desktops/)Nearly forgot about this thread. That script is pretty awesome! Thanks for the link. :)

---

### Post by agroszer on 2010-04-11
> **darthmob said:**
> Nearly forgot about this thread. That script is pretty awesome! Thanks for the link. :)
But it will need some adjustments, because it mistakenly matches text in the window title.

---

### Post by darthmob on 2010-04-12
Didn't experience any problems so far. Haven't used it that much though (only Firefox and mail).

Btw, [Kupfer]("http://kaizer.se/wiki/kupfer/") can start and detect running applications in a similar way (it either starts the application or allows you to go to one of the running instances).

---

### Post by J V on 2010-04-12
Could be done on openbox... I suppose...

---

### Post by engla on 2010-04-12
> **darthmob said:**
> Didn't experience any problems so far. Haven't used it that much though (only Firefox and mail).

Btw, [Kupfer]("http://kaizer.se/wiki/kupfer/") can start and detect running applications in a similar way (it either starts the application or allows you to go to one of the running instances).


If you [bind a trigger in Kupfer]("http://kaizer.se/wiki/log/post/Kupfer_gains_Triggers/") to the Launch action, for example Firefox &#8594; Launch, Kupfer will start the application if not running but focus it if already running. Pressing the trigger key repeatedly should switch among the application's open windows.

---

### Post by darthmob on 2010-04-12
> **engla said:**
> If you [bind a trigger in Kupfer]("http://kaizer.se/wiki/log/post/Kupfer_gains_Triggers/") to the Launch action, for example Firefox &#8594; Launch, Kupfer will start the application if not running but focus it if already running. Pressing the trigger key repeatedly should switch among the application's open windows.Nice, I didn't know those triggers were registered without Kupfer running in the foreground.

PS: I just saw you are the guy behind Kupfer. It's pretty damn Awesome (with capital A)!

---

### Post by agroszer on 2010-04-13
Here is a slightly enhanced version:
[http://blog.pyte.hu/2010/04/window-shortcuts-for-linux.html]("http://blog.pyte.hu/2010/04/window-shortcuts-for-linux.html")

---

### Post by f1r3flie on 2010-04-13
I generally do the same thing as darthmob: I have each application in a different workspace. This has lead me to run five or more workspaces at once, though, and it's becoming a headache...

---

### Post by engla on 2010-04-13
> **darthmob said:**
> Nice, I didn't know those triggers were registered without Kupfer running in the foreground.

PS: I just saw you are the guy behind Kupfer. It's pretty damn Awesome (with capital A)!

Ah, I guess you see now, that's the whole point with triggers. And why you must choose very inconvenient keyboard shortcuts for them (well) so that they don't collide with other applications.

And thanks, I think so too.

---

### Post by mellort on 2010-04-13
Hey agroszer,

wmctrl is a great tool for this task. To install it:
```
sudo apt-get install wmctrl
```
To get a feel for how it runs, open a terminal. Try running this comand:
```
wmctrl -a firefox
```
It should find the first instance of Firefox, go to the workspace it is on, and raise it to the active state. You can put the name of whatever program you want there. To make this a keyboard shortcut, go to "System > Preferences > Keyboard Shortcuts" and click on "Add" at the bottom. For the name, write something like "Go to Firefox", and for the command, write the following:
```
wmctrl -a firefox
```
Click "OK" and then scroll down to the bottom of the window. Find the command you just created, and click under the "Shortcut" column (you should see "Disabled" in the row of your command). Now, press the keys for your desired shortcut (Shift-Ctrl-Alt-F, maybe). Click "Close", and now you are finished!

Note: you can add another shortcut for any other application you want this functionality for. Just change "firefox" in the "wmctrl" command to the name of your application.

Hope this works for you.

Cheers

---

