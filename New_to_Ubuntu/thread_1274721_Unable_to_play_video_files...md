---
title: "Unable to play video files.."
date: 2009-09-24
forum: New to Ubuntu
---

### Post by mallan on 2009-09-24
I cant play any video file in by PC.When ever i play a video file the screen just goes blank for second and comes back .After it the whole system just hangs. Im using ubuntu 8.04 and my pc is lenovo g450.

---

### Post by Vaphell on 2009-09-24
which app do you use to play video clips?

try to run in terminal:
**mplayer some_clip.avi**
or **totem some_clip.avi** or whatever player you use
and see it there is anything interesting in the output in terminal.

---

### Post by mallan on 2009-09-24
i tried it,again my system got stuck  .But in the terminal there was this "failed to create dbus proxy for org.gnome.settingsDaemon:Could not get owner of name 'org.genome.SettingsDaemon':no such name

---

### Post by tuxxy on 2009-09-24
Which video formats are they, you may need to install the correct codecs first.

---

### Post by gordintoronto on 2009-09-24
> **mallan said:**
> I cant play any video file in by PC.When ever i play a video file the screen just goes blank for second and comes back .After it the whole system just hangs. Im using ubuntu 8.04 and my pc is lenovo g450.

Open a terminal window, and paste this command in:

sudo apt-get install ubuntu-restricted-extras

---

### Post by tuxxy on 2009-09-24
Also grab VLC its a great player that comes with its own codecs too;
```

sudo apt-get install vlc
```

---

### Post by ~sHyLoCk~ on 2009-09-24
I would vote for mplayer with smplayer as front-end coz of the easy tweakings. ;)

---

### Post by mallan on 2009-09-24
for any video format it is the same

---

### Post by netbook-dude on 2009-09-24
I also vote for VLC...it even works in Windows the best...

Go into terminal and type

sudo apt-get insta*ll vlc*

that should install vlc for you....good luck
[FONT=monospace]
[/FONT]

---

### Post by mallan on 2009-09-24
> **gordintoronto said:**
> Open a terminal window, and paste this command in:

sudo apt-get install ubuntu-restricted-extras

I installed it .this message appeared 

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up ubuntu-restricted-extras (15.2) ...
Setting up unrar (1:3.7.8-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


Even now it wont play any video files

---

### Post by mallan on 2009-09-24
> **tuxxy said:**
> Also grab VLC its a great player that comes with its own codecs too;
```

sudo apt-get install vlc
```
i have installed vlc....but the same story repeats...

---

