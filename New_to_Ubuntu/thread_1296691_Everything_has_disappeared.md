---
title: "Everything has disappeared"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by marcks on 2009-10-20
I am running Ubuntu 9.04

When I logged in today all I get is my background image. There are no menus, no toolbars, nothing. All I can do is Ctrl+Alt+Delete and restart.

Last night I took Evolution off (it was just locking up all the time) and added kmail.

Does anyone have any idea of what has happened.


thanks in advance
Karen

---

### Post by scragar on 2009-10-20
One of the evolution packages is a dependency for your panels and a few other things.

Use alt+f2, then type:
```
xterm
```
In there run:
```
sudo apt-get install --reinstall ubuntu-desktop
```To get everything back(hopefully), after that if you wish to remove evolution you can do so, but do not remove the data-server

```
sudo apt-get --purge autoremove evolution evolution-common evolution-exchange evolution-plugins
```

---

### Post by dominiquec on 2009-10-20
Some evolution components are dependencies of ubuntu-desktop, so if you remove them, as with "sudo apt-get remove evolution*", it will also remove ubuntu-desktop.

You can recover your desktop by running

"sudo apt-get install ubuntu-desktop"

---

### Post by Mike_IronFist on 2009-10-21
> **marcks said:**
> I am running Ubuntu 9.04

When I logged in today all I get is my background image. There are no menus, no toolbars, nothing. All I can do is Ctrl+Alt+Delete and restart.

Last night I took Evolution off (it was just locking up all the time) and added kmail.

Does anyone have any idea of what has happened.


thanks in advance
Karen

Why yes, this exact problem happened to me, in fact, not to long ago. It's nothing serious, believe it or not, but you'll have to reset your GNOME settings (which is basically your theme and other basic settings).

It's very easy to fix, just follow these instructions.

You need to write down these commands, because you can't copy and paste them:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Then press ctrl + alt + F1 and you will be whisked away to a black login screen. As usual, type in your name and press enter. This terminal will not show any password feedback as you type, so just type in your password, and press enter.

Then enter in those commands (make sure you copied them carefully, or they might not work). Afterwards, type in the following command to reboot.
```
sudo reboot
```
It will ask for your password. Once again, you get no password feedback, so just enter in your password and press enter.

---

### Post by scragar on 2009-10-21
Do not listen to mike, this is nothing to do with your config files, and even if it was the common logic would be to back them up(so you can recover things later), not delete them.

Also a complete reboot is completely unrequired for any changes to your gnome settings, restarting X will work(ctrl+alt+backspace normally).

---

### Post by Mike_IronFist on 2009-10-21
> **scragar said:**
> Do not listen to mike, this is nothing to do with your config files, and even if it was the common logic would be to back them up(so you can recover things later), not delete them.

Also a complete reboot is completely unrequired for any changes to your gnome settings, restarting X will work(ctrl+alt+backspace normally).

Whoooooa. That's awful rude, you could have spoken directly to me if you understood this problem and thought that my answer didn't apply.

I had this problem and deleting my config files fixed it exactly. If you wanted to correct me on that, you could have been a bit more polite about it.

---

### Post by scragar on 2009-10-21
> **Mike_IronFist said:**
> Whoooooa. That's awful rude, you could have spoken directly to me if you understood this problem and thought that my answer didn't apply.

I had this problem and deleting my config files fixed it exactly. If you wanted to correct me on that, you could have been a bit more polite about it.

Sorry dude, 5AM, not thinking right.

---

### Post by Mike_IronFist on 2009-10-21
> **scragar said:**
> Sorry dude, 5AM, not thinking right.

Ah. Thank you for a polite and cool-headed response.

---

### Post by marcks on 2009-10-21
thank you both

Alt+f2 didn't do anything but Ctrl+Alt+f1 brought up a terminal screen and from there I resintalled the desktop.

I had tried to reinstall from the logon area but no network.

Thank you again, it is great to be able to write to a forum and get such good help.

a very grateful
karen

---

