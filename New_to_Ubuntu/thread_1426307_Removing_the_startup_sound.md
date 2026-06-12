---
title: "Removing the startup sound"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by jermza on 2010-03-10
Is there a way to remove the startup sound (that drum beat thingy that plays when you have the type in your password)?

---

### Post by a8jr on 2010-03-10
its in the system->preferences->startup application
find "gnome login sound" then uncheck it

---

### Post by jermza on 2010-03-10
Thanks, but it made no difference.  In fact, I even removed that option from the list and I still get the startup sound (at absolute full volume for some reason).

---

### Post by sahabcse on 2010-03-10
Go to System -> Preferences -> Starup Applications
Look for &#8220;GNOME Login Sound&#8221; in the list. If you don&#8217;t want to hear anything at startup, uncheck this box.

For more info click [here]("http://ubuntulinux.co.in/blog/ubuntu/ubuntu-9-10/startup-sound-changing-in-ubuntu-9-10-karmic/")

---

### Post by marbertone on 2010-03-10
Perhaps you're italian! Go to "Sistema -> Preferenze -> Applicazioni d'avvio" and uncheck "GNOME Login Sound". It worked for me just a few days ago!
Cheers! :popcorn:
Mario Alberto

---

### Post by Ichido on 2010-03-21
How to Remove or Change the Ubuntu 9.10, Karmic's Startup Sound.

Taken from:
[http://ubuntulinux.co.in/blog/ubuntu/ubuntu-9-10/startup-sound-changing-in-ubuntu-9-10-karmic/](http://ubuntulinux.co.in/blog/ubuntu/ubuntu-9-10/startup-sound-changing-in-ubuntu-9-10-karmic/)

Step 1:
Go to System -> Preferences -> Starup Applications
Look for “GNOME Login Sound” in the list. If you don’t want to hear anything at startup, uncheck this box.
If you want to change the sound, press Edit button. Then in the command field you’ll see

/usr/bin/canberra-gtk-play –id=”desktop-login” –description=”GNOME Login”

Change “desktop-login” to the name of the sound file you want, without file extension.
Click Save and close the startup dialog.

Step 2:
Now you have to copy this new sound (.ogg or .wav file) to

/usr/share/sounds/ubuntu/stereo/

You need  root permission to copy the file into this directory which can be done by running nautilus as root.

$sudo nautilus

Then browse to that folder and paste the file there.

Step 3:
Log out and login to listen to the new startup sound.

This also works with a *.WAV Sound/File!

---

### Post by SoFl W on 2010-05-07
> **jermza said:**
> Is there a way to remove the startup sound (that drum beat thingy that plays when you have the type in your password)?

> **a8jr said:**
> its in the system->preferences->startup application
find "gnome login sound" then uncheck it

I thought I turned this off once before, now however gnome login sound does not appear in the startup application menu

I want to turn that drum beat off
I have this problem on both my 32bit laptop and my 64bit desktop.  It seems after an upgrade the startup sound returned.  (bells on the desktop, drum on the laptop)

---

### Post by geostar1024 on 2010-07-15
After some investigation of the sounds in

/usr/share/sounds/ubuntu/stereo/

I discovered that the drums sound corresponds to dialog-question.ogg, and that there is a symlink system-ready.ogg that points to it.  I renamed system-ready.ogg to system-ready1.ogg and the drums are gone! (alternatively, if you wanted a different ready sound, just point system-ready.ogg to a different sound file)

It would be nice if there was a more intuitive way to disable the system ready sound; In my opinion, it ought to be disabled when "No sounds" is selected in the Sound Preferences dialog, as that seems to turn off all other sounds.

---

### Post by wiznillyp on 2010-11-11
Is there a more elegant solution than editing the name of the file?

I have removed the startup sound from the **Startup Applications** section and that freaking sound is still annoying me.

:)

---

### Post by deepakjoy on 2010-12-07
An update for 10.04 (lucid lynx) users. To turn off the pre-login sound, go to
system -> administration -> login screen

there you will find a checkbox for disabling login sound (and also one for automatic logging in).

check out this link for screenshots [http://www.liberiangeek.net/2010/07/disableturnoff-startup-booting-sound-ubuntu-10-04-lucid-lynx/]("http://www.liberiangeek.net/2010/07/disableturnoff-startup-booting-sound-ubuntu-10-04-lucid-lynx/")

---

### Post by fanqi1234 on 2011-05-06
Thanks. Finally google directed me here so I can get the path to KILL that F***** sound.

```
sudo bash
cd /usr/share/sounds/ubuntu/stereo/
mv system-ready.ogg SHUT_UP_WHEN_READY__THANK_YOU.orz
```
:popcorn:




> **Ichido said:**
> How to Remove or Change the Ubuntu 9.10, Karmic's Startup Sound.

Taken from:
[http://ubuntulinux.co.in/blog/ubuntu/ubuntu-9-10/startup-sound-changing-in-ubuntu-9-10-karmic/](http://ubuntulinux.co.in/blog/ubuntu/ubuntu-9-10/startup-sound-changing-in-ubuntu-9-10-karmic/)

Step 1:
Go to System -> Preferences -> Starup Applications
Look for “GNOME Login Sound” in the list. If you don’t want to hear anything at startup, uncheck this box.
If you want to change the sound, press Edit button. Then in the command field you’ll see

/usr/bin/canberra-gtk-play –id=”desktop-login” –description=”GNOME Login”

Change “desktop-login” to the name of the sound file you want, without file extension.
Click Save and close the startup dialog.

Step 2:
Now you have to copy this new sound (.ogg or .wav file) to

/usr/share/sounds/ubuntu/stereo/

You need  root permission to copy the file into this directory which can be done by running nautilus as root.

$sudo nautilus

Then browse to that folder and paste the file there.

Step 3:
Log out and login to listen to the new startup sound.

This also works with a *.WAV Sound/File!

---

