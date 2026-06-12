---
title: "no sound 9.10 tried everything!"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by cairnzi on 2010-02-22
hey people, ive just upgraded ti 9.10 and have no sound at all..... installed all codecs Etc. but still no sound,i have also read loads of posts on this subject but so far no joy, i have a toshiba equium with, Card: HDA Intel
Realtek ALC861-VD

any ideas would be most appreciated, many thanks

---

### Post by mikewhatever on 2010-02-22
If installing codecs == tried everything, try following the sound solution thread.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by cairnzi on 2010-02-22
thanks, but tried what was in the post but no success..... many thanks anyway, suppose i will just have to downgrade to 9.04 for the momment, thanks anyway.:D

---

### Post by Sir Jasper on 2010-02-22
Hi,

If sound is your only problem with 9.10; then perhaps you could wait a bit longer as there are plenty of willing and knowledgeable helpers here.

I regret I do not have the experience to be of direct assistance.

My regards

---

### Post by NoaHall on 2010-02-22
Check the volume isn't muted. 

Some would recommend you do a fresh install, as it will fix it, but if you want, I have a fix - although it's not ideal.

---

### Post by cairnzi on 2010-02-23
@NoaHall i have re-installed but didnt fix the problem, what is your fix?

---

### Post by ikt on 2010-02-23
You've gone over: 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

?

---

### Post by JiuJitsu500 on 2010-02-23
type "alsamixer" in a terminal and see if anything is muted :)

Worth a shot I guess unless it's in one of those articles above....

---

### Post by cairnzi on 2010-02-24
@ikt, just went through that link you left, and the only thing that picks up my soundcard is _sudo alsa force-reload_ any ideas? but after i enter this and reboot it goes back to not detecting it,i followed all the steps as best i could, many thanks.

---

### Post by mikewhatever on 2010-02-24
You could try adding the following to /etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel mode=3stack
```

for more info on these options, check /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz.

---

### Post by cairnzi on 2010-02-24
Still not working am afraid,oh well will stick with mandriva for the moment,many thanks for the ideas.

---

### Post by no2498 on 2010-02-24
you right click the volume control yet a lot comes up try sys sounds first put something with sound play with the settings till you get sound

---

### Post by ericmarlow on 2010-02-25
> **cairnzi said:**
> hey people, ive just upgraded ti 9.10 and have no sound at all..... installed all codecs Etc. but still no sound,i have also read loads of posts on this subject but so far no joy, i have a toshiba equium with, Card: HDA Intel
Realtek ALC861-VD
 
any ideas would be most appreciated, many thanks
 
 
Sound is one of the privileges listed in User settings.
 
Try logging on as root and if it works then, go to Users and add Sound as a privilege to your normal user account.

---

### Post by ndefontenay on 2010-02-25
Hi.

I got a similar problem with my Dell Studio.

Just no sound.

Wait a sec while I look for my thread.

---

### Post by ndefontenay on 2010-02-25
OK here's what happened for me:

[http://ubuntuforums.org/showthread.php?t=1337872](http://ubuntuforums.org/showthread.php?t=1337872)

---

### Post by Alexandre Putt on 2010-02-25
Each time I update some sound related packages the sound settings are changed so that I get no output on my line out. 

OK, this may sound stupid, but have you actually checked your settings (in System->Preferences->Sound)? In particular, try changing Hardware and Output.

---

### Post by cairnzi on 2010-02-25
cheers to all,but still no joy, will just stick with xubuntu 9.10 which may i ad works no problems straight out the box and mandriva one, many thanks for the help. :)

---

