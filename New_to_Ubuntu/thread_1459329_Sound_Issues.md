---
title: "Sound Issues"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by TatoSalad on 2010-04-21
I've been trying to play some music on YouTube, but the sound refuses to play.

I don't know what the cause could be, the sound is set to 100%, and the sound isn't muted.

I'm using Realtek HD Audio.

Any ideas? :(

---

### Post by lidex on 2010-04-21
Do you have audio elsewhere?
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")
No audio at all? -> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by TatoSalad on 2010-04-27
Alright, I now have sound back.
But it seems to be quieter than usual. And the Volume Output Control on the top Taskbar has no effect whatsoever.

Apparently it has something to do with me changing something in:
System > Preferences > Multimedia Systems Selector
It's currently set to:
OSS: Open Sound System

Help? :D

---

