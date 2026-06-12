---
title: "Playing an encrypted DVD with xine"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by wolfman1221 on 2009-02-22
Hi, I recently tried to play an encrypted DVD with the Xine player, and I received this message. 

"The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"


If there is anyone who can help me with this, it would be greatly appreciated.

---

### Post by ibuclaw on 2009-02-22
The [Comprehensive Multimedia Guide]("http://ubuntuforums.org/showthread.php?t=766683") will tell you how to view encrypted DVDs, but to give a brief run down of the steps:

Add the medibuntu repository to your list of Ubuntu package sources.
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```
Get the public key and update apt.
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
And install what is needed:
```
sudo apt-get install libxine1-ffmpeg libdvdcss2 libdvdread3 libdvdnav4
```

Regards
Iain

---

### Post by wolfman1221 on 2009-02-22
It worked thanks! 

Would you happen to know how to use a c++ compiler in ubuntu like dev++?

---

