---
title: "logitech usb headset in intrepid ibex 8.10"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by nubix on 2009-02-05
is there any guide to make it fully usable? i only seem to get rhythmbox and a few other select applications.
thanks in advance for the help!

---

### Post by kostkon on 2009-02-05
Install the *PulseAudio Device Chooser*. Run it (it'll be in *Applications &#8594; Sound & Video*) and then left-click on its icon in your system tray. Select *Volume Control*. In the *Playback* tab you will see the audio streams of your various applications. Right-click on the application you want and select *Move Stream...* In the list that will appear you should see all of your audio devices listed. Select your headset to send the audio of this application to your headset.

You can set your headset as the default audio device (if you want) in the *Output Devices* tab. Right-click on it and enable the *Default* option.

For this to work you need to set all your sound playbacks in your sound preferences (i.e. in *System &#8594; Preferences &#8594; Sound*) to *Autodetect*.

You can set *PulseAudio Device Chooser* to load every time you login from its preferences.

Hope that helps.

---

