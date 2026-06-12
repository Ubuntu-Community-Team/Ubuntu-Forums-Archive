---
title: "cannot play mp3 files in VLC"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by sallam on 2010-10-09
Greetings

Playing mp3 files in VLC produces no sound. They play fine in movie player and rythbox, but not in vlc..
How can I fix this please?

---

### Post by MooPi on 2010-10-09
VLC should by default be able to play mp3 files. Can your VLC play any sound or video file ?

---

### Post by sallam on 2010-10-09
Yes, I played avi movies fine in it, with excellent sound and all.

---

### Post by TeoBigusGeekus on 2010-10-09
Do you get any message when you type in terminal
```
vlc /path/to/file/file.mp3
```

---

### Post by irv on 2010-10-09
This may sound stupid, but is you mute on in your sound setting. Mind was and I did feel stupid.
[ATTACH]171750[/ATTACH]

---

### Post by sallam on 2010-10-09
Thanks irv, but sound is not muted in my case.

TBG, it said:
> VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb75490d4, 0xb7549048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1286822124)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3431): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)

..then vlc started, file played, but no sound!
same file plays fine in other players.

---

### Post by irv on 2010-10-09
Do you have the restricted files loaded.
[ATTACH]171760[/ATTACH]

---

### Post by sallam on 2010-10-10
Do I have to?
I just tried and it warned me that the following will have to be removed:
fFmpeg codecs and utilitites

What is all this about? why onlu vlc requires all this work, while other players just run mp3 with no big deal at all?

---

### Post by Trandok on 2010-10-10
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

