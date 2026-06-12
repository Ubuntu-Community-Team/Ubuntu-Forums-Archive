---
title: "no mp3 playback"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by m_ad on 2009-07-20
I've installed the ubuntu-restricted-extras package, and I still get no mp3 playback. Audacious just freezes, and movie player just won't play it.

Using the command line, 'totem file.mp3' loads totem with no errors but just doesn't play the file.

What could be wrong?

---

### Post by NightwishFan on 2009-07-20
Perhaps you do not have all the gstreamer resources installed.

Use this command:

```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

That should work, if not, post back.

---

### Post by m_ad on 2009-07-20
Actually, I just uninstalled Audacious via Synaptic, and installed Audacious2. Playing files through Audacious2 works, but still not via totem or vlc.

```
[matt@matt-desktop:~]$ sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5 libartsc0 libaudclient1 libresid-builder0c2a libjack0.100.0-0
  libcddb2 audacious-plugins libbinio1c2 libgif4 libaudid3tag1 libmowgli1
  libfluidsynth1 libsidplay2 libmcs1 ladcca2 libimlib2 gcc-3.3-base
  libneon27-gnutls
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Since I get playback through Audacious2 (my preference), I don't mind the issue. However, it still seems something is broken.

---

### Post by NightwishFan on 2009-07-20
Try this.

```
gst-launch playbin uri=file://DRAGANDDROPMP3HERE
```

Does that play?

---

### Post by m_ad on 2009-07-20
> **NightwishFan said:**
> Try this.

```
gst-launch playbin uri=file://DRAGANDDROPMP3HERE
```

Does that play?

nope :confused:

Same behavior. Just doesn't play.

---

### Post by Eisenwinter on 2009-07-20
Do you have "lame" or "liblame" installed?

---

### Post by m_ad on 2009-07-20
I take the last comment back. I had to install gstreamer-tools.

Now I get..

```
gst-launch playbin uri=file://'/home/matt/Desktop/101.mp3' 
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstAudioSinkClock
```

with no playback.

---

### Post by m_ad on 2009-07-20
> **Eisenwinter said:**
> Do you have "lame" or "liblame" installed?

It looks like liblame0 is installed but not lame.

---

### Post by NightwishFan on 2009-07-20
I do not see how you would have missing dependencies, however, run this command just to clear that up. If it asks you to remove a bunch of stuff, do not do it. :D

```
sudo apt-get -f install
```

---

### Post by m_ad on 2009-07-20
> **NightwishFan said:**
> I do not see how you would have missing dependencies, however, run this command just to clear that up. If it asks you to remove a bunch of stuff, do not do it. :D

```
sudo apt-get -f install
```

```
[matt@matt-desktop:~]$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 libartsc0 libaudclient1 libresid-builder0c2a libjack0.100.0-0
  libcddb2 audacious-plugins libbinio1c2 libgif4 libaudid3tag1 libmowgli1
  libfluidsynth1 libsidplay2 libmcs1 ladcca2 libimlib2 gcc-3.3-base
  libneon27-gnutls
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by NightwishFan on 2009-07-20
You have no missing dependencies.. Try this:

[LIST=1]
[*]Press ALT+F2 type: gstreamer-properties and push enter.
[*]When the gstreamer-properties window opens, set for it to use ALSA under sound.
[*]Test an mp3 file
[/LIST]

---

### Post by m_ad on 2009-07-20
This didn't fix it..


I might want to add that when I try and play an mp3 file through totem, it doesn't play the file. However, it shows the visualization effects at a *very* slow rate. Causes me to believe that something is slowing down the playback.

It's weird that totem won't play the file, nor will vlc or audacious 1.5. But audacious2 will? :confused:

Thanks for your help Nightwishfan, I have to step out for a few.

---

### Post by 0x29a on 2009-07-20
Hi ya,

I can't imagine that Gnome utilities behave that much differently than KDE utilities. Try installing mpg123:
```

$ sudo aptitude install --with-recommends mpg123

```

This and lame are two sets of programs that I always seem to need to install.

Another thing to look in to is seeing if you have the mediabuntu archives added to /etc/apt/sources.list. If not, [this link]("https://help.ubuntu.com/community/Medibuntu#Adding the Repositories") will step you through that.

Good luck :)

Disclaimer: I just woke up...

---

### Post by NightwishFan on 2009-07-20
I was assuming it was a pulseaudio issue. The slow visualizations but no sound happens to me on OpenSUSE, using ALSA fixed all the problems. Well good luck, hopefully we can help you get it working.

---

### Post by m_ad on 2009-07-20
> **0x29a said:**
> Hi ya,

I can't imagine that Gnome utilities behave that much differently than KDE utilities. Try installing mpg123:
```

$ sudo aptitude install --with-recommends mpg123

```

This and lame are two sets of programs that I always seem to need to install.

Another thing to look in to is seeing if you have the mediabuntu archives added to /etc/apt/sources.list. If not, [this link]("https://help.ubuntu.com/community/Medibuntu#Adding the Repositories") will step you through that.

Good luck :)

Disclaimer: I just woke up...


Installed lame, and mpg123, didn't fix the problem. However, mpg123 uninstalled a bunch of things, including my Audacious2 :(

```
Removing audacious-plugins ...
Removing libstdc++5 ...
Removing gcc-3.3-base ...
Removing libfluidsynth1 ...
Removing ladcca2 ...
Removing libartsc0 ...
Removing libaudclient1 ...
Removing libaudid3tag1 ...
Removing libbinio1c2 ...
Removing libcddb2 ...
Removing libimlib2 ...
Removing libgif4 ...
Removing libjack0.100.0-0 ...
Removing libmcs1 ...
Removing libmowgli1 ...
Removing libneon27-gnutls ...
Removing libresid-builder0c2a ...
Removing libsidplay2 ...

```

And now Audacious2 is broken.. should have read your disclaimer :lolflag:

---

### Post by m_ad on 2009-07-20
Wow, now audacious2 won't even open a mp3 file. Installing lame and mpg123 totally broke mp3 playback.


Uninstalling mpg123 and lame, and reinstalling audacious2 didn't fix this problem. Now I have major issues.

---

### Post by NightwishFan on 2009-07-20
It should be easy to repair the damage. Just use Synaptic to install Audacious.

And while we are at it, if it is a pulseaudio issue, then this should play mp3.

```
gst-launch0.10 filesrc location=DRAGANDDROPMP3HERE ! decodebin ! osssink
```

Replace osssink with alsasink or pulsesink to test the others.

---

### Post by m_ad on 2009-07-20
Synaptic only has audacious 1.5 which is EXTREMELY buggy. I used audacious .deb packages to install 2.1 stable.

When installing mpg123, it removed a bunch of lib* files. What were these apart of? When launching audacious2 via command line, I get..

```
[matt@matt-desktop:~]$ audacious2
audacious2: error while loading shared libraries: libmowgli.so.1: cannot open shared object file: No such file or directory
```

---

### Post by NightwishFan on 2009-07-20
Ah, I see. The just remove the offending packages, and try to install the audacious deb again. If it gives you an error, install it manually, and the fix the depencies, like so.

```
sudo dpkg -i AUDACIOUSDEB && sudo apt-get -f install
```

I advise you try to find a PPA to use software, and not manual debs. I will look for an audacious ppa. For now remove the mpg package that messed everything up and follow my instructions above.

---

### Post by m_ad on 2009-07-20
Ok, I'm angry I installed mpg123.

I've reinstalled audacious2, done apt-get install -f (which didn't do anything - '0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.'), and audacious2 is still giving me the same error.

I know, I couldn't find a ppa for audacious2 :(

```
[matt@matt-desktop:~]$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  audacious-plugins
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by NightwishFan on 2009-07-20
Did the audacious.deb have any errors whilst installing? Perhaps try:

```
sudo apt-get update && sudo apt-get purge audacious2 && sudo apt-get -f install && sudo dpkg -i AUDACIOUS.DEB && sudo apt-get -f install
```

Remember to replace audacious.deb with the actual deb. Also watch if the dpkg -i command shows dependency errors.

---

### Post by m_ad on 2009-07-20
> **NightwishFan said:**
> Did the audacious.deb have any errors whilst installing? Perhaps try:

```
sudo apt-get update && sudo apt-get purge audacious2 && sudo apt-get -f install && sudo dpkg -i AUDACIOUS.DEB && sudo apt-get -f install
```

Remember to replace audacious.deb with the actual deb. Also watch if the dpkg -i command shows dependency errors.

I can't use apt-get purge audacious2..

E: Couldn't find package audacious2

---

### Post by NightwishFan on 2009-07-20
Good, it is not installed then, skip that step. (Unless the deb is not called audacious2..)

Found a PPA, might work.

[https://launchpad.net/~dupondje/+archive/ppa](https://launchpad.net/~dupondje/+archive/ppa)

Remember to add the jaunty sources, not karmic. (You are using jaunty correct?)

---

### Post by m_ad on 2009-07-20
> **NightwishFan said:**
> Good, it is not installed then, skip that step. (Unless the deb is not called audacious2..)

Found a PPA, might work.

[https://launchpad.net/~dupondje/+archive/ppa](https://launchpad.net/~dupondje/+archive/ppa)

Remember to add the jaunty sources, not karmic. (You are using jaunty correct?)

Cool, sorry I'm a newb. How do I add the above ppa to sources.lst?

Nope, I'm using Hardy.

---

### Post by m_ad on 2009-07-20
By the way, the debs are

audacious_2.0.1-1_i386.deb
audacious-plugins_2.0.1-1_i386.deb

When entering audacious2 in the terminal, I get

```
audacious2: error while loading shared libraries: libmowgli.so.1: cannot open shared object file: No such file or directory
```

```
[matt@matt-desktop:~/Documents]$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  audacious-plugins
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

installing mpg123 and lame broke my audacious2

I went through and reinstalled everything that mpg123 uninstalled. Audacious2 now works, but I know I did something wrong..

Nightwishfan, if I want to install audacious2 on hardy, instead of audacious1.5 which is in the repos (which is buggy as heck), how can I do it the right way?

---

### Post by NightwishFan on 2009-07-22
First off, remove any packages associated with Audacious and mpg123. (Unless the are needed for ubuntu-desktop)

I cannot seem to find anyway to install Audacious2 for Hardy, so I would just rely on the source you originally used.

---

### Post by m_ad on 2009-07-22
Thanks again for your help.

---

