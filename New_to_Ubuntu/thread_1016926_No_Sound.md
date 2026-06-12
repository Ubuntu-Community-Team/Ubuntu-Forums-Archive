---
title: "No Sound"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by sctb082552 on 2008-12-20
This is my sound card controller according to the device manager


IXP SB400 AC'97 Audio Controller

I have no sound.  What can I do?

All help appreciated

---

### Post by ets2006 on 2008-12-20
i am assuming that your soundcard is a laptop onboard card...
go to system>preferences>sound and change the values in the drop downs.. play with them and use the test button - if you have sound, it's working!


[https://answers.launchpad.net/ubuntu/+question/19955](https://answers.launchpad.net/ubuntu/+question/19955)

---

### Post by sctb082552 on 2008-12-20
Some more clarification; Sorry

It is a laptop built in speakers.  They worked when I had XP on the system. 8.10 is the only OS on the computer now.

all speaker volumes are set at high.

I have just tried the test in the configuration and inserting a CD with no noise.

Thanks for your assistance

---

### Post by ets2006 on 2008-12-20
if you go to system>preferences>sound and change the values in the drop downs.. play with the values and use the test button to check - if you can hear sound, it will be working.

another thing to check - you said it was a laptop, have use used the keyboard buttons for turning the hardware volume up - some laptops are quirky like that. My ibm t23 used to boot with the hardware volume at zero!

---

### Post by kansasnoob on 2008-12-20
I always start here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Basically start by going to Terminal and post the output of:

```
aplay -l
```

My second step is to install gnome-alsamixer. It's in synaptic or:

```
sudo apt-get install gnome-alsamixer
```

There are other ways of accessing all of the controls but that puts them all in one gui:

[ATTACH]97071[/ATTACH]

[ATTACH]97072[/ATTACH]

Since you have NO sound whatsoever I doubt it's a pulse audio problem but if so you'd want to look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Pay special attention to Note #1.

---

