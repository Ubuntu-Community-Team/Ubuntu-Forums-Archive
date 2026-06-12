---
title: "[SOLVED] Sound on internet not working on Intrepid"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by richie42 on 2009-01-11
So what is happening is that I updated from hardy to intrepid. Today I noticed that whenever I go onto anything on the Internet like You-Tube or any website that has sound, I cannot hear anything. I can hear that bongo sound when I turn the computer on and the funny clicking sound when I log in. If I go into my music files, I can hear things, but I cannot hear anything when I go on anything involving the Internet...

---

### Post by RomeReactor on 2009-01-11
Hi. Have you switched everything in the "Devices" tab in 'System->Preferences->Sound' to PulseAudio Sound Server? Do you have any media players or games running when this happens? If PulseAudio is already running, have you tried killing the process?
```
pkill pulseaudio
```

---

### Post by richie42 on 2009-01-11
For the record, I am basically computer illiterate, so everything except for terminal (I figured that out a month ago), just confused the heck out of me.

Sorry.

---

### Post by RomeReactor on 2009-01-11
Alright, let's try this first: in the menu on the top panel, go to 'System->Preferences->Sound' and on the first tab (named "Devices") you should see four sound-related dropdown menus (see attached picture). Make sure all four are set to **PulseAudio Sound Server**; close the application, then in Firefox reload the page with the video, or close Firefox and open it again and then try to see the video.

---

### Post by richie42 on 2009-01-11
I tried that... It's still not working...

---

### Post by RomeReactor on 2009-01-11
Does this problem happen only with Flash videos, or with videos playing in the Totem (or VLC, or Mplayer) plugin in Firefox? Make sure the volume in the video player isn't muted or all the way down.

Do you have any other applications (games, media players) running at the same time when this happens?

---

### Post by richie42 on 2009-01-11
Well, I can run music files that are on my comp on Totem and it is fine. I mean, I can't think of any websites that have non-flash sound items, though so that would be my problem with checking that it is just a flash problem.

---

### Post by RomeReactor on 2009-01-11
Do you know whether you have Flash or Gnash installed? (Gnash is an Open Source Flash plugin that usually causes conflicts with Flash, if Flash is installed as well). Please open a new tab in Firefox and paste this in the address bar:
```
about:plugins
```
Look for the entry for Flash and post which plugin is active.

---

### Post by richie42 on 2009-01-11
```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

There you go...

---

### Post by RomeReactor on 2009-01-11
> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124


You seem to have an older version of the Flash plugin; if you installed it from the repositories (using Synaptic or Add-Remove, or from the terminal with Apt-Get or Aptitude), close Firefox and try uninstalling the Flash plugin:
```
sudo aptitude purge flashplugin-nonfree
```
Then update your repository information:
```
sudo aptitude update
```
And then install Flash again:
```
sudo aptitude install flashplugin-nonfree
```

Then open Firefox again and see if the problem is still there.

---

### Post by richie42 on 2009-01-11
Thanks, IT WORKED!!!!!

The song that i first listened to was [http://www.youtube.com/watch?v=kB7IsMnbC88](http://www.youtube.com/watch?v=kB7IsMnbC88), so that was really appropriate. 

Thanks, again.

:guitar:

---

### Post by RomeReactor on 2009-01-11
You're welcome. Glad you sorted it out :popcorn:

---

