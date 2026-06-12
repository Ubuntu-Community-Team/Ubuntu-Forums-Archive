---
title: "Customize the login screen in Ubuntu 10.04 ?"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by chrisdee on 2010-07-17
Hi.

I wonder if it's possible to customize the Ubuntu 10.04 login screen. How is this done and what files are involved ?

I want to add a link to an external windows terminal server.



Thanks.

---

### Post by arrimapirate on 2010-07-17
Other than changing the background, i dont believe it is possible to customize it. I would love to be proven wrong though as i dislike the current GDM

---

### Post by kerry_s on 2010-07-17
> **chrisdee said:**
> Hi.

I wonder if it's possible to customize the Ubuntu 10.04 login screen. How is this done and what files are involved ?

I want to add a link to an external windows terminal server.



Thanks.

i think the 1 you want is "**/usr/share/xsessions**"

for doing custom look, background, theme, pointer:
**gksudo -u gdm dbus-launch gnome-appearance-properties**

---

### Post by ieee488 on 2010-07-17
> **kerry_s said:**
> i think the 1 you want is "**/usr/share/xsessions**"

for doing custom look, background, theme, pointer:
**gksudo -u gdm dbus-launch gnome-appearance-properties**

That command does not let you change the login screen.

From what I have read and tried, changing the login screen even just the background is a pain in the neck.


By the way, executing that command causes TWO Universal Access Properties icon to appear on the top panel. SIGH.

---

### Post by kgas on 2010-07-17
You can change the b/g, lot of tutorials out there. Try this [one](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)

---

### Post by sisco311 on 2010-07-17
> **ieee488 said:**
> That command does not let you change the login screen.

From what I have read and tried, changing the login screen even just the background is a pain in the neck.


That command allows you to change the theme, wallpaper, icons, fonts and mouse cursor of the login window.

> **ieee488 said:**
> 
By the way, executing that command causes TWO Universal Access Properties icon to appear on the top panel. SIGH.

```
sudo -u gdm killall gnome-settings-daemon
```should kill UAP.


@OP: 

Have a look at the documentation: 
[http://library.gnome.org/admin/gdm/2.30/gdm.html](http://library.gnome.org/admin/gdm/2.30/gdm.html)

/usr/share/gdm/autostart/LoginWindow/ contains the .desktop files of the auto-started application.

---

### Post by kerry_s on 2010-07-17
> **ieee488 said:**
> That command does not let you change the login screen.

From what I have read and tried, changing the login screen even just the background is a pain in the neck.


By the way, executing that command causes TWO Universal Access Properties icon to appear on the top panel. SIGH.

just go to system-> preferences-> keyboard, accessibility tab & uncheck it. when you log out & back in uap won't appear no more.

it does work. i changed the background, theme, cursor & font on mine.

---

### Post by spydeyrch on 2010-07-17
I would recommend ubuntu tweak. It is a simple program that allows you to change a plethora of options, background, windows command buttons, login screen, splash screen, etc etc. I always install it on every install that I do.

[Ubuntu Tweak Stable]("http://ubuntu-tweak.com/source/ubuntu-tweak-stable/")

Just add the ppa to your sources via the terminal, pretty simple to do so. ;)

-Spydey :P

---

### Post by ieee488 on 2010-07-17
> **kerry_s said:**
> 

it does work. i changed the background, theme, cursor & font on mine.
I can do that too.

No, the OP is talking about the **login** screen, not the desktop once you are logged in.

---

### Post by arrimapirate on 2010-07-17
Ubuntu Tweak will let you change a lot of settings but the GDM is untheamable now : (

Why is Ubuntu getting harder and harder to personalize with each release?

---

### Post by kerry_s on 2010-07-17
> **ieee488 said:**
> I can do that too.

No, the OP is talking about the **login** screen, not the desktop once you are logged in.

i am talking about the log in screen! read better!

---

### Post by techunit on 2010-07-17
Canonical wanted a standard log-in screen to represent there OS.

---

### Post by Izkata on 2010-07-17
Ubuntu Tweak would be the best one to go with if all you want to do is change the background.  **Scratch that:  I just installed Ubuntu Tweak, and the option to change the background is not there.**

If you also want to change stuff like the window manager, font, and other controls (as I don't like the way some look), here's the simplest way to gain access to Appearance Properties while in the Login screen:

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

Now log out.  The Appearance changer will pop up on top of the login window.  Make the changes you want - themes, background, etc, and close it.  Then log back in, and remove the file so it doesn't happen each time:

```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by techunit on 2010-07-18
> **Izkata said:**
> Ubuntu Tweak would be the best one to go with if all you want to do is change the background.  **Scratch that:  I just installed Ubuntu Tweak, and the option to change the background is not there.**

If you also want to change stuff like the window manager, font, and other controls (as I don't like the way some look), here's the simplest way to gain access to Appearance Properties while in the Login screen:

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

Now log out.  The Appearance changer will pop up on top of the login window.  Make the changes you want - themes, background, etc, and close it.  Then log back in, and remove the file so it doesn't happen each time:

```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
I just installed Ubuntu Tweak and I can still change the background of the log-in screen.

---

### Post by arrimapirate on 2010-07-18
> **techunit said:**
> I just installed Ubuntu Tweak and I can still change the background of the log-in screen.

Really? i still can and its up to date. You have to hit the unlock button in the bottom right corner to be able to make changes.

---

### Post by techunit on 2010-07-18
> **arrimapirate said:**
> Really? i still can and its up to date. You have to hit the unlock button in the bottom right corner to be able to make changes.
Exactly

---

### Post by chrisdee on 2010-07-20
Thanks for all of your answers. But does anybody know how I can add a simple link to a remote terminalserver in the login screen ?

---

### Post by sisco311 on 2010-07-20
> **chrisdee said:**
> Thanks for all of your answers. But does anybody know how I can add a simple link to a remote terminalserver in the login screen ?

Sorry, I don't understand. What do you mean by a "simple link"?

---

### Post by kerry_s on 2010-07-20
> **chrisdee said:**
> Thanks for all of your answers. But does anybody know how I can add a simple link to a remote terminalserver in the login screen ?

/usr/share/xsessions
you need to make a *.desktop file with the command. look at the others.

---

### Post by chrisdee on 2010-07-20
> **sisco311 said:**
> Sorry, I don't understand. What do you mean by a "simple link"?

Sorry if I'm unclear. Let me try to explain better.

There is a command called rdesktop with wich I can connect to terminal servers
from the Ubuntu 10.04 shell/command line.

Below is an example :
rdesktop -g 100% terminal.server.com

Instead of having to run this command from command line I'm looking for a way to put it in the login window.
This way users can just click on it if they want to login to e.g a windows terminal server instead of loggin in to Ubuntu 10.04.

I hope I'm clear enough ?

---

### Post by tarps87 on 2010-07-20
I do not believe this is possible, however a solution could be to set up the guest account (no password needed, and I think it still exists in 10.04) and then set a task to run redesktop with the correct arguments.

---

### Post by chrisdee on 2010-07-20
Ok, thanks. Strange thow, because it was possible in 9.04. There is a computerlab here at the university with this setup.

---

### Post by tarps87 on 2010-07-20
> **chrisdee said:**
> Ok, thanks. Strange thow, because it was possible in 9.04. There is a computerlab here at the university with this setup.

I that case it is likely it is still possible, I was not aware of it being done before. Do you have any details on the 9.04 setup?

---

### Post by proxess on 2010-07-20
GDM Setup (somewhere in the PPAs) allows you to change the login background and icons.

---

### Post by tarps87 on 2010-07-20
The issues as I understand it is not related to backgrounds or icon, instead the op wants to add a link/button that when selected launches redesktop or a similar program, with will allow a user to connect to a windows computer remotely.
I know it is or at least was possible to connect to a Linux based box in such a way but was not aware of it being able to connect to a windows box. However the op has mention a previous setup is it was at least possible.

---

### Post by chrisdee on 2010-07-20
> **kerry_s said:**
> /usr/share/xsessions
you need to make a *.desktop file with the command. look at the others.

Thanks. I could not figure out much from the contents of those files. You know of any examples ?

---

### Post by chrisdee on 2010-07-21
> **tarps87 said:**
> the op wants to add a link/button that when selected launches redesktop or a similar program, with will allow a user to connect to a windows computer remotely.


Correct.

Any ideas ?

---

### Post by spydeyrch on 2010-07-21
Well, I think that on the ubuntu tweak site, there is a program called GDM2. I haven't used it and don't have very many details. Plus I think that it is in a beta stage right now. But, from what I understand, and again this is going off of very little info, it seems that it allows one to change the login info. It might be what you are after.

There is also on that same site XSplash Background Settings. Look here to find both of them (ignore the third one in the list):

[http://ubuntu-tweak.com/app/search/?q=GDM](http://ubuntu-tweak.com/app/search/?q=GDM)

Let me know if it helps. 

Again, I haven't used either of them before but they might contain what you need. :D

-Spydey :KS

---

### Post by mcduck on 2010-07-21
While I don't think there's any way to add your remote desktop directly as a visible button in GDM, you *can* add one as a selectable option under the sessions-menu (together with Gnome, xterm session and any other desktop environments etc. you might have available).

Here's a basic guide for creating custom X sessions: [https://wiki.ubuntu.com/CustomXSession]("https://wiki.ubuntu.com/CustomXSession")

---

### Post by chrisdee on 2010-07-24
Thanks.

---

### Post by SEECo on 2010-07-30
I can tell you just go to the the login screen and press ctrl+alt+f1.Once you did this enter your login name and hit enter. After that type 'export DISPALY=0.0' and againhit enter.And now type 'sudo -u gdm gnome-control-center, again hit enter. now wait 8 to 10 seconds and pres ctrl+alt=f7. And you will see that the tty1 has been finished and a dialog has been appeared . In that dialog box click appearance and again a dialog box will appear in that dialog box make changes you want and click close. And close the control center and you will see your login screen customized as you want.

---

