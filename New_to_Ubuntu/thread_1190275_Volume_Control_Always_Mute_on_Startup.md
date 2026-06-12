---
title: "Volume Control Always Mute on Startup"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2009-06-17
Is there any way that I can have the volume control turned on when I start Jaunty?  It is always mute on startup and then I have to turn mute off.  I am using pulseaudio.

Thanks for any help in advance.

---

### Post by LewRockwell on 2009-06-17
some folks are having success with this:

[http://ubuntuforums.org/showthread.php?p=7159816#post7159816](http://ubuntuforums.org/showthread.php?p=7159816#post7159816)

---

### Post by arnold.pietersen on 2009-06-21
It worked.

Thanks a lot.

Arnold

---

### Post by dano1 on 2009-06-23
had the same problem. made sure pulseaudio-module-x11 and hal(pulseaudio-module-hal) were loaded through syanptic. Then checked user and root under pulse and haldaemon in users and groups. All works fine, no need for the startup script anymore.  

hth, danny

---

### Post by arnold.pietersen on 2009-06-23
Hi Dano1

I removed pulseaudio and is using ALSA instead.  Sound is there when I startup, but somehow the sound disappears.  Tells me that the device is being used by another application.  Then I have to restart the laptop. I tried to use ps -ef to see which program might be grabbing the sound, but there are too many lines you have to read through.

I am glad you go your sound working.

---

