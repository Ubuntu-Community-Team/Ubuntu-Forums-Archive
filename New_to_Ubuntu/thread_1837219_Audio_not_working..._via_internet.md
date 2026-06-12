---
title: "Audio not working... via internet"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by Nagle75 on 2011-09-01
I have no clue why, but out of no where my internet audio stopped working. I can still hear music through my music player & I can also hear the default sounds that Ubuntu makes when it starts up. However, any audio coming from the internet, be it youtube, or any other kind of streaming audio, I cannot hear. I'm not one to tinker w/ the settings, so all I can think of is that maybe an update I installed some how borked my audio settings??? I found another thread where someone had a similar problem, & so I tried to run the following in a terminal window...
$ sudo apt-get install libflashsupport
[sudo] password for nagle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
I have no idea what could possibly be wrong, or how to fix it. Any help would be GREATLY appreciated!

---

### Post by androssofer on 2011-09-01
> **Nagle75 said:**
> I have no clue why, but out of no where my internet audio stopped working. I can still hear music through my music player & I can also hear the default sounds that Ubuntu makes when it starts up. However, any audio coming from the internet, be it youtube, or any other kind of streaming audio, I cannot hear. I'm not one to tinker w/ the settings, so all I can think of is that maybe an update I installed some how borked my audio settings??? I found another thread where someone had a similar problem, & so I tried to run the following in a terminal window...
$ sudo apt-get install libflashsupport
[sudo] password for nagle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
I have no idea what could possibly be wrong, or how to fix it. Any help would be GREATLY appreciated!

try this: [http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

---

### Post by Nagle75 on 2011-09-01
I read this thread & but I still couldn't get it to work. I tried it on firefox, although I've been using Chromium as my default browser. When I got to the point where you're supposed to open gksudo gedit /etc/firefox/firefoxrc... They say that you should see this... FIREFOX_DSP=”none”... well, when I opened gedit, it was blank... nothing... so then I cut, & pasted FIREFOX_DSP=”aoss” into gedit & saved it, & then restarted firefox & still nothing.

---

### Post by Redmage913 on 2011-09-01
Do you have the ubuntu-restricted-extras package installed? It includes many packages that may help your problem with audio.

---

### Post by ENigma885 on 2011-09-01
This libflashsupport fix is ancient now. Since Ubuntu Hardy 8.04, u don't have to do any workarounds because Pulse Audio has become the uniform audio server in the system.

So, it will be appreciated if you provide your Ubuntu version; though I suppose it's 8.04, at least, or later. If it's the case just install Flash player installer by 

```
sudo apt-get install flashplugin-installer
```

**Note:**
Because of the rapid development process of Linux distros and specifically Ubuntu, when u follow a forum thread make sure it's a recent one.

---

### Post by Nagle75 on 2011-09-01
I'm running Maverick Meerkat 10.10. Sorry, I didn't realize that thread was old & I didn't know what else to try, it's the only thing I've come across thus far that's similar to my issue. I just did this: 


nagle@nagle-G41D3:~$ sudo apt-get install flashplugin-installer
[sudo] password for nagle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  lirc libftdi1 python-mutagen setserial libcdio-dev libiso9660-dev videotrans
  libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ENigma885 on 2011-09-01
mm..OK let's make sure that the problem is as I diagnosed.
**1-** Play any Youtube video and check if ALSA plug-in appears in the "Sound Preferences" Application's tab
*System>>Preferences>>Sound* then *Application* tab
if it doesn't appear, it's not using PulseAudio as I suggested.

**2-** So, we will make sure that PulseAudio is configured as the default audio server; open a terminal window and paste ```
gstreamer-properties
```
then select *"PulseAudio Sound Server"*  from the drop down menu of *"Output"*

Just to clarify, I'm not sure what you exactly did in your desperate tries to make it work. Unfortunately, it might be a lil bit difficult to fix.

---

### Post by Nagle75 on 2011-09-01
Ok... I've never used Pulse audio before, so I ran the command you suggested & it opened a box & I selected Pulse & then saved it. As I was doing that, it said this in the terminal window... I'm not sure if it's helpful or not. Just to reiterate, the only thing I tried was on the very first page of that thread, which was suggested to me above. Other than that, I haven't tried anything else.

---

### Post by Nagle75 on 2011-09-01
nagle@nagle-G41D3:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

---

### Post by Nagle75 on 2011-09-01
Still nothing... under sound prefs it says Alsa-Plugin, but nothing about Pulse.

---

### Post by ENigma885 on 2011-09-01
- These messages are not of any significance.
- What's important here is that "ALSA-Plugin" appearing in sound preferences means that Flash plugin is using PulseAudio and it's configured properly.
- You should not "use" Pulse; it's configured by default and you should not, normally, do any further configuration after installing your system.

**Hints that might help:**
1- Restart your browser and may be the whole system just to be sure.
2- Check if the "ALSA-Plugin" in sound preferences is muted or reduced in sound.
3- Make sure the Youtube audio is not muted or whatever media you are streaming.

---

### Post by Nagle75 on 2011-09-01
Ok... so I feel rather embarrassed, but I figured it out. The audio on youtube was slid all the way down. I still think it's completely bizarre as I never tinker with making adjustments like that. I must've been tired when I did that! Arrrggghhh!!! :redface:

---

### Post by ENigma885 on 2011-09-02
ha ha it always happens indeed; great that u can now hear your "muted" videos on Youtube =)

---

