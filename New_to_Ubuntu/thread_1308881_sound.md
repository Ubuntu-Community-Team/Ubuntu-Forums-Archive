---
title: "sound"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by mitchay on 2009-11-01
absolute newbie (69 year old beginner), have just installed easypeasy, working fine
but no sound whatsover, have read thru most forums on this but nothing seems to help,
how can I get my sound back ?  have toshiba nb205 netbook.

---

### Post by sickly on 2009-11-01
i had the same issue and this worked for me,
 
open terminal and type
 
 
 
gksudo gedit /etc/modprobe.d/alsa-base.conf 
 
 
 
type your password when promted and add these lines to the end of the file that opens
 
 
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1 
 
 
 
 
 
Then save and reboot

---

### Post by sseelbinder on 2009-11-01
Same problem with my Toshiba NB205.  Sickly's recommendation did not resolve the issue.

I did a clean install with UNR 9.10, and the internal speaker still doesn't work.  I was really hoping that it would have been resolved in UNR 9.10.

Also, it appears as though my internet connection has slowed down considerably after going from 9.4 to 9.10.

Waiting patiently for updates.......

---

