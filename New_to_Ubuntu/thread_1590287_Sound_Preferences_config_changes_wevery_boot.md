---
title: "Sound Preferences config changes w/every boot"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-10-07
On boot, my System/Preferences/Sound/Sound Preferences/**Input** shows two available choices:

1 - Internal Audio Analog Stereo

or

2 - 0807 Analog Mono

Even though I mouse click the 2nd (Analog Mono), on reboot the system defaults to the 1st. (Analog Stereo). As my Skype will only have a microphone with the Analog Mono selected, can someone tell me how to make this the default?

---

### Post by cariboo on 2010-10-08
Try using alsamixer to set the default sound device:

[list]
[*] press F6 to select the device
[*] press esc to exit
[*] type **sudo alsactl store** to save your changes
[/list]

---

