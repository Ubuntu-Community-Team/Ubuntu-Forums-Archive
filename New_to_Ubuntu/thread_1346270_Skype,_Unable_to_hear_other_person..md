---
title: "Skype, Unable to hear other person."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by mastermael on 2009-12-04
On skype static, I cannot hear the other person, my volume works fine and i can hear other things, Can anybody help me? (they can hear me)

---

### Post by lisati on 2009-12-04
It might not be your fault. If you can hear other things it's likely the person at the other end has to set up their microphone. Ask them to do a test call using Skype's call testing service. It probably won't hurt for you to do a quick check with Skype's call testing service either.

---

### Post by mastermael on 2009-12-04
They can be heard by other people, i cannot even hear the test call person/bot.

---

### Post by lisati on 2009-12-04
You might want to tinker with Skype's options and choose a different playback device. They can be accessed by right-clicking on the Skype icon then "options"

---

### Post by meho_r on 2009-12-04
1. Make sure your audio settings are all "pulseaudio", then make test sound and test call.

2. You may try skype from [Medibuntu](https://help.ubuntu.com/community/Medibuntu) repository since it solves problems with camera which are present in skype from official skype.com website.

---

### Post by mastermael on 2009-12-04
The option was the wrong one, Thank you!

---

### Post by mastermael on 2009-12-06
When i tried to call my friend this morning, i got the same problem, he can talk to others fine, i cannot hear him though. the options are exactly the same as last night, when i was talking to him fine, and hadnt changed a single setting.

---

### Post by mastermael on 2009-12-06
Can anyone help me? I really would like to talk to my friends, as they live in different states/countrys.

---

### Post by meho_r on 2009-12-07
1. Double check audio settings in skype. All should be pulseaudio.

2. Check your sound settings (System > Preferences > Sound). Pay attention to "Hardware" tab: under "Profiles" you should make sure to pick the correct profile (if there are many of them, you'll have to try one by one and see which works; generally, you should use the one that has "input" and "output" in its name, e.g., "Analog Surround 7.1 Output + Analog Stereo Input). Then check your microphone (tab "Input" in "Sound preferences"; NOTE: you may not actually hear your voice, just pay attention to input level metter: it will show if microphone works). If microphone works and you can hear audio from any audio player, (re)start skype and do a test call.

---

### Post by diablo75 on 2009-12-07
There is a bug with Skype and Pulse Audio that hasn't been worked out yet, hence the "Beta" in the name of the latest version out.  I tried this version a while ago and had to revert to the previous because I couldn't hear anything, and all they could hear was a loud static noise.

Recently, medibuntu updated their repositories and I found it upgraded my copy of Skype to the version I tried to avoid a month or two earlier.  To revert this time, I did the following:

In terminal:

```
sudo apt-get remove skype skype-common
```

Then, download these two files:

[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb)

[http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb)

Install the "skype-common" deb file first by double-clicking on it after it's downloaded.  Then do the same thing with the skype deb package.

That should install skype, 2.0.0.72.  I got a "break" error when I did this, but ignored it and found Skype worked.

The last thing you'll want to do is open System>Administration>Synaptic Package Manager, search for "skype", click on the name then click (at the top) Package>Lock Version.  This will prevent it from updating to the next version.

---

