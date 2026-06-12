---
title: "Need help getting sound on new install"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2009-02-26
I just canned vista and moved into ubuntu on this machine. I am not a total n00b but I have no sound any help please?

---

### Post by halitech on 2009-02-26
whats the output of ```
aplay -l
```

also, what are you trying to get to play? (ie. mp3, wav, videos?)

---

### Post by DarkSaga70 on 2009-02-26
> **halitech said:**
> whats the output of ```
aplay -l
```

also, what are you trying to get to play? (ie. mp3, wav, videos?)

betty@betty-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Trying to get stream sound mp3 so on.. Amarok's shoutcast says no availible decoder?

---

### Post by halitech on 2009-02-26
so sound devices looks okay. Did you install the multimedia codecs?

---

### Post by DarkSaga70 on 2009-02-26
> **halitech said:**
> so sound devices looks okay. Did you install the multimedia codecs?

no i didn't can you walk me through that please?

---

### Post by halitech on 2009-02-26
all the info you need is here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by DarkSaga70 on 2009-02-26
when I type the  commands I get this?
betty@betty-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for betty: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
betty@betty-desktop:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
betty@betty-desktop:~$

---

### Post by kansasnoob on 2009-02-26
I'd suggest two things:

(1) Install gnome-alsamixer from synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Lots of toggles, pay special attention to the first three and the last four (VIA) toggles, and whether or not you have an external amp (even USB)!

(2) Assuming this is 8.04 or 8.10 go here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by DarkSaga70 on 2009-02-26
I have some sound like system sound now but not able to get past another problem. But thank you for the help on this one. Hopefully the new one I started will get me to the end of this set up.

---

### Post by halitech on 2009-02-26
> **DarkSaga70 said:**
> when I type the  commands I get this?
betty@betty-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for betty: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
betty@betty-desktop:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
betty@betty-desktop:~$

when you tried this, did you have Synaptic open as well?

---

### Post by markbuntu on 2009-02-27
Just go here, it is all explained in a very easy way and no confusing terminal activities involved.


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

