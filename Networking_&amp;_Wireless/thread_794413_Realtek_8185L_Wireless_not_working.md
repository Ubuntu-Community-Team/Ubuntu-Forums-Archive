---
title: "Realtek 8185L Wireless not working"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Master_Z on 2008-05-14
I am running Hardy Heron (8.04). My Wireless card is the realtek 8185L. My wired connection works fine, but it wont show my wireless. I type in lshw -C network and it shows my wireless. Any way to get my wireless to work?

---

### Post by chili555 on 2008-05-14
You might try here: [http://ubuntuforums.org/showthread.php?t=646320](http://ubuntuforums.org/showthread.php?t=646320)

---

### Post by Master_Z on 2008-05-14
I got it working!! Here's how:

1) Download ndisgtk from snaptics package manager.
2) go to system, administration, windows wireless drivers.
3) install the new file (XP driver for your wireless card) by browsing and selecting it. 
4) It should install quickly and say hardware present. 
5) Left click your network icon on your taskbar and it should have your access points! Enjoy!

---

### Post by chili555 on 2008-05-14
Glad you got it going so quickly and easily and thank you very much for posting your solution for the searchers. I recommend you edit the title of the thread to add SOLVED. Thanks.

---

