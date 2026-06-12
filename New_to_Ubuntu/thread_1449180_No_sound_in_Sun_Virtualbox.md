---
title: "No sound in Sun Virtualbox"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by iosef86 on 2010-04-07
Hi, I'm using Windows XP and running Ubuntu on a Sun Virtualbox, and I've seen other posts relating to the fact that there's sometimes no sound, most of the solutions dealt with switching the audio host driver from Null Audio to something else in the settings, but I tried that and it still isn't giving me any sound, my only options were Null Audio and Windows DirectSound, which it's set to, and audio is enabled, but still nothing, Does anyone have any ideas what might be wrong? Much appreciated, Thanks!

---

### Post by Chronon on 2010-04-07
Make sure mixer levels are turned up in Ubuntu.  You might try installing/running alsamixer and making sure the levels are turned up.

---

### Post by iosef86 on 2010-04-07
Thanks, Where would I find the mixer levels? I'm fairly new to Ubuntu, Also I just checked the Hardware Drivers and the PC Speaker driver isn't activated, could that be the problem? When I try to activate it it asks for an authorization key, but as far as I know I don't have one....

---

### Post by Chronon on 2010-04-07
If it asks for authorization try using your user's password that you use for login.

Open the Software Center and install alsamixer if it isn't installed already.  Once you have verified that it is installed select the terminal from the Gnome menu.  Just type in "alsamixer" and press Enter to start the program.  You can check the sound levels for various channels (PCM, Front, Back, etc.).

You can also check to make sure PulseAudio isn't muted by using PulseAudio Volume Control (pavucontrol).

---

### Post by iosef86 on 2010-04-07
I don't use a password for login, it's never asked for one,  And It wants the password to install Alsamixer as well :( Is there a way to reset it?

---

### Post by Chronon on 2010-04-07
When you installed Ubuntu inside of Virtualbox it should have asked you to set a username and a password.

Before trying anything else, go to the Virtualbox settings for the Ubuntu virtual machine.  You may wish to make sure that "Audio Controller" is set to "ICH AC'97", according to a post I found on the Virtualbox forums:
> The sound adapter must be the ICH AC'97 in Ubuntu guest settings.
[http://forums.virtualbox.org/viewtopic.php?f=3&t=25926](http://forums.virtualbox.org/viewtopic.php?f=3&t=25926)

---

### Post by iosef86 on 2010-04-07
The thing is I wasn't the one who set up the Virtualbox, A local computer shop did it for me, What I should probably do is ask them if they can tell me what the password is, The Audio Controller is already set to AC97, I have a feeling it's probably due to the inactive PC-Speaker Driver, Thanks for all your input by the way,

---

### Post by mikodo on 2010-04-07
I don't have an answer to solve your difficulties, but I think AC'97 are the audio codecs for Vista and Windows 7. The answer probably is something else, other than using AC'97 drivers for Linux.

I guess I'm wrong about the audio driver for a guest ubuntu in a XP host. I followed the link provided earlier in this thread and Perryg (a regular on the Sun Vbox site), does say that in this setup you should be using the ICH AC'97 drivers. I set up a guest Windows 7 in Karmic host and had to install Realtek AC'97 drivers then, for the Windows7. That's what made me think that the ICH AC'97 driver would be the wrong one. for you...Sorry

Good Luck

---

