---
title: "Problems with speaker system"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Sentoguy on 2010-03-27
Hello,

I've followed the tutorial on upgrading my alsa version to 1.0.22.1 and have successfully done so. But Ubuntu is still not recognizing/responding to my speaker system.

For reference I am using a Dell Inspiron Zino and have the following sound cards have been detected by Ubuntu:
hda-intel ATI Technologies Inc sBx00 Azalia (Intel HDA)
hda-intel ATI Technologies Inc RS780 Azalia controller
legacy Probe legacy ISA (non-PnP) chips 

Does anyone else have a Dell Zino and had the same problem? I'm running Ubuntu 9.10 btw and think it's the newest kernel version, but not sure how to find out.

I also know that it's not the speaker, because Windows 7 (which came installed on the computer) responds to them just fine.

Thanks in advance for any help.

---

### Post by rockerphil on 2010-03-27
have you checked the ALSA mixer settings? this can be done either through the terminal by running 

```
alsamixer
```

then using the arrow keys to make adjustments, or if you want a point and click GUI you can install the package alsamixergui by running this command in the terminal

```
sudo apt-get install alsamixergui
```

then simply run the command 

```
alsamixergui
```

from the terminal. hope this helps,

Phil

---

