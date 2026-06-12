---
title: "vlc player in terminal...shall code"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by coolmego on 2011-02-11
I am new in linux and using ubuntu10.10 and trying to learn shell scripting..wenever i type this command i.e " vls <some video name>" this sequence of process takes place...can i know what are those means..i have pasted the code from the shell..you can look through it...
"PC:~/Desktop$ vlc Facebook.flv
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x896f914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb667d0d4, 0xb667d048)
Warning: call to signal(13, 0x1)
[flv @ 0xb7318190]Estimating duration from bitrate, this may be inaccurate
Warning: call to signal(13, 0x1)
Warning: call to srand(1297497725)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2914): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
[flv @ 0x8c85d50]Estimating duration from bitrate, this may be inaccurate"

---

### Post by thefasterblueone on 2011-02-11
VLC seems to be looking for Facebook.flv on your system and is not finding it.
Is Facebook.flv on your system or the web?

---

