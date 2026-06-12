---
title: "Sound"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by mcicero on 2009-03-08
I have just installed ubuntu 8.10 on my Dell Latitude D830 laptop.  After installing java and flash I found that now I have no sound.  I ran the system test to confirm this.  How can I fix this problem.

---

### Post by sandyd on 2009-03-08
can you do 

```

lspci
```
in terminal?

---

### Post by paydaydaddy on 2009-03-08
Take a look at the thread linked below and see if it helps. If you have a hard time following any part of the suggested operations post back for specific help.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by kansasnoob on 2009-03-08
I'd begin with the Basic Troubleshooting Steps here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Basically just to be sure your sound card is recognized.

I also like to install "gnome-alsamixer" from synaptic which will then show up in Sound & Video. (It makes tweaking controls very simple). Pay special attention to the first three and last four (VIA) toggles, and also the external amp "tick" if it applies.

You may also find this helpful (I have a number of times):

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

