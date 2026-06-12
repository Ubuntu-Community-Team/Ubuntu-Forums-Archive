---
title: "What controls the LOGIN jingle ?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by davexnet on 2010-05-04
Hello -
I've got two users set up on my Ubuntu Karmic,
when I login with one, you get the opening drum roll but nothing else.

However, logging in as the more-recently-created-user,
you get the drum roll followed by the jingle.

Where is this controlled from?  Is there a LOGIN script somewhere?
TIA for any info.

---

### Post by DigitalDakness on 2010-05-04
I second this guys . . . .

---

### Post by pjones0404 on 2010-05-04
I am pretty sure that you should click on the speaker icon in the panel and go to sound preferences and set the theme to  no sound,

---

### Post by Arla on 2010-05-04
Nevermind, I found mine, it's under System > Preferences > Login Window (there is play sound option).

What I'm not seeing (in either spot) is WHAT sound is played, just whether the sound is played or not.

Seems to have been made harder since Karmic (from all my googling) so far I've found check what GNOME Login Sound has under System > Preferences > Startup Applications

Mine has /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

---

### Post by lessmemorelove on 2010-05-04
check your control panel under startup applications. it is called gnome login sound:p

---

### Post by lessmemorelove on 2010-05-04
> **Arla said:**
> Hijacking (maybe slightly) where does one control the sound when the login window is shown, not when you login, but when the login window shows, because I'd really like to NOT have a sound there, but can't figure where that is either...

under gconf-editor go to apps->gdm->simple-greeter->sound

---

### Post by davexnet on 2010-05-05
In system /preferences/startup/GNOME login sound 
you see the command /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

If I execute this command from a Terminal, it plays the jingle
in my second user ID, but not in the first.

I'm still none the wiser about what's really going on.


Arla mentioned this:
"Nevermind, I found mine, it's under System > Preferences > Login Window (there is play sound option)."

But I don't have a "login Window" selection under "preferences".

---

### Post by Didius Falco on 2010-05-05
> **davexnet said:**
> In system /preferences/startup/GNOME login sound 
you see the command /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

If I execute this command from a Terminal, it plays the jingle
in my second user ID, but not in the first.

I'm still none the wiser about what's really going on.


Arla mentioned this:
"Nevermind, I found mine, it's under System > Preferences > Login Window (there is play sound option)."

But I don't have a "login Window" selection under "preferences".

How to Remove or Change the Ubuntu Startup Sound.


Step 1:
Go to System -> Preferences -> Startup Applications
Look for “GNOME Login Sound” in the list. If you don’t want to hear anything at startup, uncheck this box.
If you want to change the sound, press Edit button. Then in the command field you’ll see

/usr/bin/canberra-gtk-play –id=”desktop-login” –description=”GNOME Login”

Change “desktop-login” to the name of the sound file you want, without file extension.
Click Save and close the startup dialog.

Step 2:
Now you have to copy this new sound (.ogg or .wav file) to

> /usr/share/sounds/ubuntu/stereo/

You need root permission to copy the file into this directory which can be done by running nautilus as root from the Terminal.

```
sudo nautilus
```

Then browse to that folder and paste the file there.

Step 3:
Log out and login to listen to the new startup sound.

This also works with a .WAV files.

Regards,

Didius

---

### Post by davexnet on 2010-05-05
Thanks Didius,

Regarding this problem, the command line seem to be in place,
I haven't changed it, just trying to play the default sound.
The ogg file is in the correct folder but it still doesn't play.

Unfortunately I've had some niggling things like this since
I did the 9.04 > 9.10 upgrade.  I'm going to install
9.10 fresh tomorrow and go from there.

---

