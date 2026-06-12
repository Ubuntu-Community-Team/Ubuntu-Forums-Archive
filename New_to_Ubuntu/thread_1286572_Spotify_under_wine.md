---
title: "Spotify under wine"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by fixerman on 2009-10-09
I have installed Wine and then Spotify. It all went to plan and I listened to all my music for an hour or so and then I shut it down. Now I cannot see how to run the newly installed Spotify. I cannot seem to find an icon for it anywhere. :confused:
Please advise.

---

### Post by MelDJ on 2009-10-09
under applications-wine-programs?

---

### Post by gjoellee on 2009-10-09
You can find applications installed with WINE, in the menu section for WINE. If not you can find spotify.exe (used to start spotify) under /home/$user/.wine/drive_c/Program Files/Spotify  (or something similar to that path)

---

### Post by guriinii on 2009-10-09
There also should be a "spotify.ink" file in the /home/$user/.wine/drive_c/Program Files/Spotify or put on your desktop, which can be dragged onto the quick launcher bar at the top of the screen.

---

### Post by random turnip on 2009-10-09
Applications --> Wine --> just look through the list for Spotify, if it isn't there then have a look in the virtual C drive.

---

### Post by fixerman on 2009-10-09
Found it thanks!:P

---

### Post by guriinii on 2009-10-09
Your welcome! Happy to help a fellow noob.

---

### Post by peakshysteria on 2009-10-10
> **guriinii said:**
> There also should be a "spotify.ink" file in the /home/$user/.wine/drive_c/Program Files/Spotify or put on your desktop, which can be dragged onto the quick launcher bar at the top of the screen.

I've just installed Wine and Spotify. I must say I really don't know my way around Wine yet. I've ran in to some boring problems:

1. To open Spotify with Wine I have to open the terminal and:

```
wine "C:\Program Files\Spotify\spotify.exe"
```

Or go to /home/$user/.wine/drive_c/Program Files/Spotify and right-click Spotify.exe and open with Wine. I can't fine another way to run it.

2. Choppy playback. Premium account.

I followed the instructions on the Spotify site:

```
winecfg
```

Go to the Audio tab in the program and click on Test Sound. If you hear something, then you are all set, if an error message appears you have to configure it. Make sure the ALSA checkbox is checked and press OK and restart winecfg (it needs to re-initialize sound drivers) and click on Test Sound again. When you hear something you can continue. If you can&#8217;t get sound to work, it is unlikely you will hear anything in Spotify.

In the DirectSound frame at the bottom enter the following for best sound.

Hardware Acceleration: Emulation
Default Sample Rate: 44100
Default Bits Per Sample: 16
Driver Emulation: unchecked

I have also tried to Enable high bitrate + Use at most 10 GB. Last.Fm scrobbling is also enabled.

Can anyone help to enable smooth playback and to make a shortcut either to applications or the panel?

---

