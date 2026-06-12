---
title: "no audio"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by karasuhebi on 2008-12-05
Total newbie to Linux/Ubuntu. Installed the restricted extras package. Can view YouTube videos and such, but no audio anywhere on the comp. Help?

-karasuhebi

---

### Post by opscure on 2008-12-05
open up a terminal and type alsamixer.  Make sure your volume is turned up.  Hit escape to exit alsamixer.

---

### Post by karasuhebi on 2008-12-05
tried that. it's all the way up. any other ideas?

---

### Post by karasuhebi on 2008-12-05
I also tried this:
[http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html](http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html)

still no sound.

---

### Post by karasuhebi on 2008-12-06
Um...help? Please? :D (AKA bump)

---

### Post by kansasnoob on 2008-12-06
If you have no sound at all look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

If you have very weak sound install:

```
sudo apt-get install gnome-alsamixer
```

You'll see it in Sound & Video, pay special attention to the first three and last four (via) toggles.

---

### Post by kansasnoob on 2008-12-06
On second thought we have not even done the basics:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by karasuhebi on 2008-12-13
I did the troubleshooting and got all the way up to this section:
[https://help.ubuntu.com/community/SoundTroubleshooting#Manual](https://help.ubuntu.com/community/SoundTroubleshooting#Manual) Installation

Specifically, I did everything up to the "Refreshing/Reinstalling the drivers" section. After the end of that section, I did nothing. I don't want to manually get new drivers.

And I still have no sound. What do you suggest I do next?

---

### Post by karasuhebi on 2008-12-16
Any other suggestions? :-D

---

### Post by thaltek on 2008-12-18
maybe... i am not fully sure if they are related but in order to play .flv files from my system i had to download the gsteamer plugins for totem media player to play the files....

---

### Post by karasuhebi on 2008-12-18
That could be one of the problems, but I don't think so. I'm not getting any audio at all. Not even when the system boots up.

---

### Post by karasuhebi on 2009-01-05
Does anyone else have any suggestions? I've been looking around some Linux forums, but I still have no sound. :-(

---

