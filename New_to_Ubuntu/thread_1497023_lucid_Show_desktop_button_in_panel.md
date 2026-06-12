---
title: "lucid: Show desktop button in panel"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-05-30
Recently installed kubuntu-desktop after default Ubuntu (gnome) installation. Liking the new kde4 so far. However, there is no "Show Desktop" button in panel.
So this is what I did. First assigned a shortcut key to ShowDesktop via "Global Shortcutkeys"

```

KMenu > Search > Shortcut > Global Keyboard Shorcuts 
KDE component: KWin > Show Desktop > Ctrl+F11

```Tested it by pressing Ctrl+F11: works. Then installed xdotool 

```
sudo apt-get install xdotool
```Then created a 2 line script "showdesktop"

```
#!/bin/bash
xdotool key Ctrl+F11
```Made the script executable 
```
chmod +x showdesktop
```and copied it to my $HOME/bin directory.
Then using the quick launcher in the panel created a "ShowDesktop"
launcher. This created a file

```
$HOME/.local/share/applications/showdesktop.desktop
```Opened this file to change StartupNotify to false

```
StartupNotify=false

```Everything done. Now however when I click on the button, the windows
sometimes blinks and other times keeps popping up and down. Sometimes the
panel and the screen also gets frozen. To test it whether this also happened from the terminal typed 

```
xdotool key Ctrl+F11
```in the terminal. Even then screen starts blinking!!! Other shortcut keys work nicely. Like

```
xdotool key Ctrl+F12
```which shows the dashboard. 

SO, now my question, is this happening to anybody else too. If yes, then any reason why "Show Desktop" shortcut key would not work from the terminal via xdotool?

---

### Post by ankspo71 on 2010-05-30
Hi,
Have you tried right clicking on the panel, then selecting Panel Options > Add Widgets > then pick the "show desktop" widget? Or is it missing from there too? That widget also has keyboard shortcut configurations, just like the others do.

Check to see if you have plasma-widgets-addons and plasma-widgets-workspace installed. I can't say for sure if those include the show desktop widget, but it seems like it would.
Hope this helps. (see screenshots too)

---

### Post by a.sarkar on 2010-05-30
Thanks ankspo71. The plasma-widgets-addons package did the trick :). It is not part of default kubuntu-desktop package, but part of recommended packages. Since I had disabled installation of recommended packages, it didn't get installed.

Marking this thread as solved.

---

