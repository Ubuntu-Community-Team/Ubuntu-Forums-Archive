---
title: "How do I get better sound quality from Virtualbox?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-25
Hey,
got virtualbox running with Windows XP and when I play sound within it, like an mp3, it's all choppy and broken, like it's not streaming from the virtual pc.

Any ideas how to get this fixed?

---

### Post by UbuntuNerd on 2009-03-25
did you enable the "alsa" audio drivers under the virtual machine settings?

---

### Post by Gp. on 2009-03-25
Yep

---

### Post by gorucan on 2009-03-25
Why do you need to play those files through virtualbox...
just copy them to some place on hard disk and play them on main os. =)

---

### Post by Gp. on 2009-03-26
Because I'm running Cubase in the virtualbox.

And Guitar Pro...

---

### Post by medya on 2010-02-10
I have the same problem , this fixed many people's problem who had the same problem with me and you :

[http://forums.virtualbox.org/viewtopic.php?p=51237#p51237](http://forums.virtualbox.org/viewtopic.php?p=51237#p51237)


but it hasnt fixed my problem yet :(

---

### Post by gauda_78 on 2010-04-07
I had same problem. I solved it by changing the host audio driver in virtualbox audio settings
from pulseaudio to OSS audio driver. I got a warning about sound-something but I ignored it
and everything worked perfect! :)
try it, maybe it helps. :)

---

