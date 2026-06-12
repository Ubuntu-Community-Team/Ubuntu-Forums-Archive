---
title: "cant't get any audio at all"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by phantom16 on 2009-05-25
For the past couple weeks i have been turning my computer into a media machine, and the current problem i'm facing is i can't get any audio at all to play. i have searched all over the internet for my other problems and have managed to solve them all off of reading other sites, or solve them mostly (i still cant get wireless top work, just stuck being hardwired). anyways i cant find out how to get ANY audio. i have searched and even gone as far as doing something on one forums and i downloaded an entire alsa package of 4 and did all that, but to no avail and i just need help please.

---

### Post by 73ckn797 on 2009-05-25
It could be as simple as right clicking on the speaker icon on the upper desktop panel and selecting volume control. Once there make sure the levels are adjusted up and that none of the individual controls are muted which can be seen on the icon below each level adjuster.

---

### Post by phantom16 on 2009-05-25
i have done that, and gone through all 9 devices in the drop down menu and put all them up as well. i have also put up the audio in all the applications im trying to play things from (namely rhythmbox and VLC)

---

### Post by Steelmourne on 2009-05-25
Type this command in terminal and post what comes up:

lspci -vv | grep Audio

Might be a driver issue. What device comes up?

---

### Post by phantom16 on 2009-05-25
> **Steelmourne said:**
> Type this command in terminal and post what comes up:

lspci -vv | grep Audio

Might be a driver issue. What device comes up?

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

---

### Post by Steelmourne on 2009-05-25
This should help: [http://ubuntuforums.org/showthread.php?t=1088978](http://ubuntuforums.org/showthread.php?t=1088978)

Also have you tried testing sound under system and preferences? Does the sound work or is there nothing?

---

