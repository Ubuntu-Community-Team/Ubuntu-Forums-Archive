---
title: "Sound card not being detected"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by banerjeerupak on 2010-05-01
I have just upgraded to 10.04. Everything is working just fine. In fact i really like the transition to the latest firefox version. 

But my sound card is not responding. I can not change the volume on my system. My speakers are working and there is sound. But i can't change the volume. Also even if my earphones are connected, the speakers keep working. Might have got into a mess at my workplace today. 

How to resolve it?

---

### Post by lidex on 2010-05-01
When you say you cannot change volume, are you saying your volume control doesn't do anything or you don't have a volume control?

---

### Post by banerjeerupak on 2010-05-02
The volume control icon is present but it doesn't do anything. Also when i go to sounds from Preferences, it just says waiting for sound card to respond.

---

### Post by FoxMcCloudwp on 2010-05-02
Try changing the volume in the Terminal

```
alsamixer
```

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by banerjeerupak on 2010-05-02
The output from the commands that you wanted me to execute are

root@blitzkreig:~# uname -a
Linux blitzkreig 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

root@blitzkreig:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

root@blitzkreig:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

root@blitzkreig:~# head -n 1 /proc/asound/card*/codec#*

Hope that helps. And you can help me to sort out the problem. 

Thanks a lot
The help is deeply appreciated. 
Codec: Analog Devices AD1981

---

### Post by lidex on 2010-05-02
What is the make/model of your PC/Laptop?

---

### Post by banerjeerupak on 2010-05-02
I'm using a Compaq NX6325 by HP. It is a 2006 model. Was working perfectly with 9.10.

---

### Post by lidex on 2010-05-02
If it was working with karmic it should work here. Have you tried alsamixer? Also try gnome-alsamixer (in the repo's if not installed) and make sure to enable all options in "Edit> Sound Card Properties". For alsamixer:
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

One more thing - have seen botched alsa installs latety. Try upgrading it referencing this post:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

---

### Post by banerjeerupak on 2010-05-03
Thank you so much for walking me through this. I remember that even for 9.10 i had used alsamixer to sort out the sound once and so it was easy thereafter. 

Thanks again. 

Rupak

---

