---
title: "Sound not working -"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by dmcdaniel on 2009-11-30
I am getting the following error:

```
No volume control GStreamer plugins and/or devices found
```

I am also getting this error in the Sound section under System - Preferences - sound when I try to test playback on Autodetect:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

When I run gstreamer-properties - I tried to change it from Autodetect to ALSA but it failed to detect sound. 

I know the sound works because it works in Windows.

---

### Post by phillw on 2009-11-30
> **dmcdaniel said:**
> I am getting the following error:

```
No volume control GStreamer plugins and/or devices found
```I am also getting this error in the Sound section under System - Preferences - sound when I try to test playback on Autodetect:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```When I run gstreamer-properties - I tried to change it from Autodetect to ALSA but it failed to detect sound. 

I know the sound works because it works in Windows.


Have a look over here -->  [http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)

Regards,

Phill.

---

### Post by dmcdaniel on 2009-11-30
> **phillw said:**
> Have a look over here -->  [http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)

Regards,

Phill.

Phill,

I am using Ubuntu 8.04 not 9.04. I am also using Gnome if that helps. None of that information in the thread appeared to be related to what I am experiencing.

---

