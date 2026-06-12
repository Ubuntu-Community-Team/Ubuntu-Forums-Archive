---
title: "Sound not working on computer"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by kroni_hunter on 2010-09-27
I have installed Ubuntu and I have managed to get youtube videos to play and avi videos to play, but the sound is not working whatsoever.  What specific drivers or codecs do I need to get the sound to work on my computer?

---

### Post by andrewthomas on 2010-09-27
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by kroni_hunter on 2010-09-29
For some reason, whenever I try to use these guides they don't seem to help very much.  It's all a lot of technical jargon and I honestly have no idea how to go about following the instructions.  

First of all, I have an ASUS M4A79XTD EVO and I am using an onboard sound card.  And the speakers I am using are inside of my TV which is connected via HDMI.  I am not sure if all the drivers are installed and I do not know how or where to find them.

EDIT:  After looking at sound preferences, I saw that there is nothing under the Input tab.

---

### Post by cjv8888 on 2010-09-29
Have you looked at the mixer to make sure that the outputs are not muted?

```
alsamixer
```

---

### Post by garvinrick4 on 2010-09-29
> **kroni_hunter said:**
> I have installed Ubuntu and I have managed to get youtube videos to play and avi videos to play, but the sound is not working whatsoever.  What specific drivers or codecs do I need to get the sound to work on my computer?
```
sudo apt-get install ubuntu-restricted-extras
```
start here and report back, this is all types of things you need.

 First go to software sources in System/Administration and make sure your repositories on checked to be available. universe-multiverse-restricted turn them all on. then reload or
go to a terminal and:
```
sudo apt-get update
```

---

### Post by garvinrick4 on 2010-09-29
Sound preferences to hardware to profile, I do believe there is a HDMI selection.
On my television Sony 40 inch. There are only 32 inch drivers available in kernel for
Sony running a HDMI to HDMI. So I am out of luck there. I do believe with the televisions
as monitors if they got drivers they do, if they do not they do not and that is the way it is.

---

