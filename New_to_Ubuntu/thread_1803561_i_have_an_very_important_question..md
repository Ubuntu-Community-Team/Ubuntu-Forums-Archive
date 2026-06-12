---
title: "i have an very important question."
date: 2011-07-13
forum: New to Ubuntu
---

### Post by ufo2222 on 2011-07-13
Hello. I would like to know how much space ubuntu takes up on my hard drive i currenty have windows 7 installed and i installed it inside of windows for 30 gigs but i would ike to know what that means and i will be able to exede that limit and if it will erase my files and stuff. Tahnks

---

### Post by seawolf167 on 2011-07-13
Welcome to the forums!

It sounds like you did a Wubi installation and set the virtual partition size to 30GB. This space is available to your Ubuntu partition (think *file* as this is a Wubi install), and *can* be increased, but is much easier to set it at the correct size the first time. 30GB will be more than enough for your purposes provided you are not storing tons of videos, music, etc. on your Ubuntu install.

---

### Post by ufo2222 on 2011-07-13
Thank you. i am just ocd about hard disk space.

---

### Post by seawolf167 on 2011-07-13
You should be good to go for a long long while with a 30 GB partition. There is a Wubi guide available [here]("https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c"), and if you do end up needing to resize your Wubi partition, you can follow the instructions [here ]("http://ubuntuforums.org/showthread.php?t=1625371")to do so.

Please don't forget to mark the thread as solved under thread tools if you got everything solved.

---

### Post by Rubi1200 on 2011-07-13
+1 to the great links posted by seawolf167.

As a precaution, make a backup copy of the root.disk and store it somewhere safe such as an external medium.

Also, as pointed out, 30GB should be more than enough space. You may want to consider storing personal data and large files somewhere other than the root.disk.

Enjoy!

---

