---
title: "New Firefox problem - No min/max/close buttons ?"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by mistypotato on 2009-10-12
Hi,

Yesterday I updated my system and now Firefox is acting odd.

I updated to 3.0.14

The Minimize, Maximize and Close buttons at the top, right are missing?
So I have to use the text menu on the left to close or minimize Firefox.

Also missing is the top bar that should say "Firefox"

No other application is doing this.

Thanks for any suggestions.

---

### Post by laidback on 2009-10-12
Try pressing F11

---

### Post by bobbob1016 on 2009-10-12
And mark the thread as Solved when you get a working solution.

---

### Post by wojox on 2009-10-12
Try turning off desktop effects and see if that does anything.

---

### Post by diablo75 on 2009-10-12
> **laidback said:**
> Try pressing F11

Press F11 twice.

I've seen this problem before.  Firefox will start in non-fullscreen mode and the size of the window is just beyond the resolution of the display, so the upper edge of the window is there (with the menus and all) but it's hanging off and can't be seen at first.  Hitting F11 twice will make it go full screen, then bring it back to windowed and resize the window down to fit the monitor.

A way to fix this is to hit F11 twice, then un-maximize the window and use the mouse to resize the window to something just under fullscreen so it is all visible.  Then close the Firefox window.  When you re-open it from here on out it should always start at the size you left it when you closed it, which should make the entire window visible and solve your problem.

---

### Post by fbugnon on 2009-10-12
I have not a clue why this is happening, but since is only doing with Firefox, my guess would be to try to reinstall Firefox, specially with the --purge option (to make sure the problems is not within your personal preferences), but in this case make sure you back up your Bookmarks or any other password Firefox is memorizing for you.

To simply reinstall (with no preferences lost - but smaller change of solving your problem), TRY:

```
$ sudo aptitude reinstall firefox

```

Or if you want to try reinstall _without keeping your preferences_, TRY:

```
$ sudo aptitude remove --purge firefox && sudo aptitude install firefox

```
Hope it helps

---

### Post by 150pilot on 2009-10-12
[http://ubuntuforums.org/showthread.php?t=1001223]("http://ubuntuforums.org/showthread.php?t=1001223")

This worked for me when this happened to me.

Charles

---

### Post by ChildOfMana on 2009-10-12
Are you using Compiz (desktop effects)?

I was having this problem also. All you need to do (assuming you *are* running Compiz) is go to CompizConfig Settings Manager (under *System > Preferences*), click on *Utility* on the left hand side, then click on *Workarounds* and take the tick out of the box that says *Legacy Fullscreen Support*. Should do the trick :)

if you're running Compiz but haven't got Settings Manager installed then simply open a Terminal and type:

```
sudo apt-get install compizconfig-settings-manager
```

Hope this helps.

---

### Post by mcduck on 2009-10-12
> **fbugnon said:**
> I have not a clue why this is happening, but since is only doing with Firefox, my guess would be to try to reinstall Firefox, specially with the --purge option (to make sure the problems is not within your personal preferences), but in this case make sure you back up your Bookmarks or any other password Firefox is memorizing for you.

To simply reinstall (with no preferences lost - but smaller change of solving your problem), TRY:

```
$ sudo aptitude reinstall firefox

```

Or if you want to try reinstall _without keeping your preferences_, TRY:

```
$ sudo aptitude remove --purge firefox && sudo aptitude install firefox

```
Hope it helps

"--purge" won't touch user's personal preferences. No option in any package management tool does that. They belong to that user, so admin tools should never touch them. The only way to remove user's personal settings is to do it manually.

"--purge" removes the *system-wide* configuration files.

---

### Post by lovinglinux on 2009-10-13
See **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002).

---

### Post by thnkfreely on 2010-11-05
Thanks diablo75!  What you said fixed if for me.  So simple, yet effective.  What relief after trying so many more involved fixes.

[/quote] A way to fix this is to hit F11 twice, then un-maximize the window and use the mouse to resize the window to something just under fullscreen so it is all visible.  Then close the Firefox window.  When you re-open it from here on out it should always start at the size you left it when you closed it, which should make the entire window visible and solve your problem.[/QUOTE]

---

