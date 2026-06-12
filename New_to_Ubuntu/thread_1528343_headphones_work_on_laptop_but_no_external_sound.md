---
title: "headphones work on laptop but no external sound"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by eyeofreason on 2010-07-10
I'm running Mint 9. I have headphones but no external. I've exhausted google can aybody help?

---

### Post by eyeofreason on 2010-07-10
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dana@dana-laptop ~ $ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
dana@dana-laptop ~ $ head -n 1 /proc/asound/card*/codec#*

---

### Post by lidex on 2010-07-10
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

