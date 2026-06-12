---
title: "Disabling wm"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Fizzzy on 2010-06-09
Hello,
So I took the bold choice and tried to install awesomewm using a tutorial ([http://ubuntuforums.org/showthread.php?t=678902]("http://ubuntuforums.org/showthread.php?t=678902")), and it failed, possibly because I have two monitors.

I want to disable it from starting when I boot however, because my wm is messed up when I login, I can't navigate correctly to the boot settings menu.

Is there any way to fix this, or am I better off reinstalling?

---

### Post by mbzn on 2010-06-09
Go System>Preferences>Startup Applications and just un(tick) it

---

### Post by Fizzzy on 2010-06-09
> **mbzn said:**
> Go System>Preferences>Startup Applications and just un(tick) it

That's my problem, I can't get there after I login.
(I'm running Windows now on a different partition)

---

### Post by Zemblan on 2010-06-09
Can you not just change the session type using GDM? There should be an option to choose gnome or whatever else you have.

If your GUI is not working you can run commands by pressing cntrl-alt-f1 to switch to a virtual terminal and logging in there.

EDIT: In those instructions it has you create a awesome.desktop file to give you a session option for awesome in GDM, so there should be alternatives in the menu. You could just delete the file /usr/share/xsessions/awesome.desktop using the virtual terminal

```
sudo rm /usr/share/xsessions/awesome.desktop
```

Then GDM will default to one of the other entries.

---

### Post by Fizzzy on 2010-06-09
> **Zemblan said:**
> Can you not just change the session type using GDM? There should be an option to choose gnome or whatever else you have.
You might try:

```
sudo aptitude reinstall ubuntu-desktop
```

If your GUI is not working you can run that command by pressing cntrl-alt-f1 to switch to a virtual terminal and log in there.

Alternatively just go to the virtual terminal as mentioned above and remove awesomewm.

That didn't seem to do the trick for me, what would be the best way to remove awesomewm via the terminal?

Edit: Just saw your edit, trying that now

**Edit (again):** That didn't seem to do the trick, it awesomewm still loads after I login

---

### Post by Zemblan on 2010-06-09
Yes, shouldn't edit away my laziness, I just hadn't looked very closely at the instructions in the thread. When I did I realised what I said probably wouldn't work.

---

### Post by Zemblan on 2010-06-09
Did you edit your .xinitrc file, and add a line like 'exec awesome' there?

---

### Post by Fizzzy on 2010-06-09
> **Zemblan said:**
> Did you edit your .xinitrc file, and add a line like 'exec awesome' there?

I don't think so, I pretty much just followed the main part of the tutorial word for word.

---

### Post by Fizzzy on 2010-06-09
If it helps, one monitor is displaying awesomewm, and one is displaying the normal GDM thing (toolbar part that comes with ubuntu, not sure if that's the correct name), but it doesn't work if I click on anything in the GDM toolbar.

It's also not letting me right click on anything, but from what I've heard that's normal in awesomewm.

---

### Post by Zemblan on 2010-06-09
Ah ok, something of a misunderstanding here. GDM is the Gnome Desktop Manager, you can think of it as being the screen that comes up when you boot and asks you to put in your password (assuming you haven't got it set to log you in automatically)

Should look something like: 

[IMG]http://farm3.static.flickr.com/2775/4504018626_2babda5648.jpg[/IMG]

Down at the bottom you should be able to click and choose a session.

---

### Post by Fizzzy on 2010-06-09
> **Zemblan said:**
> Ah ok, something of a misunderstanding here. GDM is the Gnome Desktop Manager, you can think of it as being the screen that comes up when you boot and asks you to put in your password (assuming you haven't got it set to log you in automatically)

Should look something like: 

[IMG]http://farm3.static.flickr.com/2775/4504018626_2babda5648.jpg[/IMG]

Down at the bottom you should be able to click and choose a session.

I remember something being there, but there's nothing at the bottom of the login screen now

---

### Post by Zemblan on 2010-06-09
After you have clicked on your name do you not see a menu bar at the bottom that looks like [this?]("http://dl.dropbox.com/u/5066517/Screenshot-2.png")

---

### Post by Fizzzy on 2010-06-09
> **Zemblan said:**
> After you have clicked on your name do you not see a menu bar at the bottom that looks like [this?]("http://dl.dropbox.com/u/5066517/Screenshot-2.png")

Haha, you're right, I have to click my name first, excuse my stupidity.

I see four options there:
```
Failsafe GNOME
GNOME (in italics)
KDE
xterm
```

---

### Post by angry_johnnie on 2010-06-09
try gnome session.

if it does the same, see what the gnome session is invoking:

```
cat /usr/share/xsessions/gnome.desktop
```

should yield this:

```
[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0

```

if the Exec line is anything other than gnome-session, then just change it.

```
sudo nano /usr/share/xsessions/gnome.desktop
```

change it, and use ctrl + o to save and ctrl + x to exit.

try it again.

if you do not find /usr/share/xsessions/gnome.desktop, then create it.

if it continues, then the problem is with gnome-session,  more than likely.

you could re configure

```
sudo dpkg-reconfigure gnome-session
```

or just reinstall.

```
sudo apt-get install --reinstall gnome-session
```

if it persists, (darn...) you could try reconfiguring the whole desktop

```
sudo dpkg-reconfigure ubuntu-desktop
```

or reinstalling it.

---

