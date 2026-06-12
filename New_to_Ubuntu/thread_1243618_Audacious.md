---
title: "Audacious"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by xtrmzero on 2009-08-18
i have some problems with audacious. it seemed to work fine until i tried to use winamp 2 skins on it. it worked very well first time i aplied the skins, but after a restart it didnt work anymore. it runs but it doesnt play any songs.
i realy love this player and i`d like to know how to fix this.

please help a noob :D

---

### Post by Perfect Storm on 2009-08-18
Try this;

Open the terminal (Applications ---> Accessories ---> Terminal)

and type;
```
audacious
```
Please post the output of the terminal.

---

### Post by Jose Catre-Vandis on 2009-08-18
Also, go into preferences > audio and try changing to alsa - away from pulse-audio

---

### Post by xtrmzero on 2009-08-20
when i write audacious in a terminal it runs, the player apears on the desktop, functional in every way but it cannot play anything. it doesnt matter what song it doesnt work. i can do anything whith the preferences and everything else......just like before

anyway this is what it says in the terminal. maybe u`ll figure it out:

amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded

---

### Post by mc4man on 2009-08-20
try using a new config, either browse to manually or
```
 mv ~/.config/audacious/config ~/.config/audacious/config.bak
```

Then open audaciuous and ck., if needed open preferences and reset any changes  (audio ouput ect.

To revert back to current config if a reset wasn't of any use

 ```
mv ~/.config/audacious/config.bak ~/.config/audacious/config

```

---

### Post by xtrmzero on 2009-08-20
doesnt work.
this is what it says:

xtrmzero@xtrmzero-desktop:~$  mv ~/.config/audacious/config ~/.config/audacious/config.bak
xtrmzero@xtrmzero-desktop:~$ audacious
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:7880): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:7880): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin


after playing around:

** (audacious:7880): WARNING **: alsa_setup(): Sample format not available for playback: Invalid argument
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:7880): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed

** (audacious:7880): WARNING **: alsa_setup(): Sample format not available for playback: Invalid argument
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:7880): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed
amidi-plug(i_backend.c:i_backend_unload:164): unloading backend 'alsa'
amidi-plug(i_backend.c:i_backend_unload:167): backend 'alsa' unloaded
LASTFM: (cleanup) Cleanup finished
xtrmzero@xtrmzero-desktop:~$ mv ~/.config/audacious/config.bak ~/.config/audacious/config
xtrmzero@xtrmzero-desktop:~$ 

and...that it :(

---

### Post by xtrmzero on 2009-08-20
ok i tried this: alt+F2 then gksudo than audacious and it works
however, if i try to run it as user it doesnt work

any thoughts on why is that?

---

### Post by xtrmzero on 2009-08-20
never mind my last plea :)

i got it working again

i took every setting form the preferences of the working audacious under root and compared to the not working one for the user.

AT LAAAAASTT SKINNZZZ. :D     :guitar:

Thanks guys, thank u for everything.

---

