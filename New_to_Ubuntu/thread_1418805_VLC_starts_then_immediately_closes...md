---
title: "VLC starts then immediately closes.."
date: 2010-03-01
forum: New to Ubuntu
---

### Post by hopelessone on 2010-03-01
Hi All,

> blade@blade:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x1c9d888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x30d6f78] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  103
  Current serial number in output stream:  104
blade@blade:~$ 

How can i fix this?

All video files suddenly did this...tried reinstall deleting all traces of vlc..

---

### Post by 3rdalbum on 2010-03-01
Have you removed the VLC preferences file/folder that's in a hidden folder in your home directory?

---

### Post by hopelessone on 2010-03-01
Hi,

Do you know exactly where it is?

Thanks..

---

### Post by hopelessone on 2010-03-01
OK fixed it by setting it to: [OpenGL Video Output] in preferences of VLC...

---

### Post by 3rdalbum on 2010-03-01
~/.config/vlc

(the 'vlc' folder inside the .config folder in your home directory - delete that and see how you go)

---

### Post by jimstar79 on 2012-04-01
> **3rdalbum said:**
> ~/.config/vlc

(the 'vlc' folder inside the .config folder in your home directory - delete that and see how you go)

Hi mate, 

I know this is an old thread but just wanted to say that this fixed it for me - and just wanted to say thanks!! 

:KS

---

