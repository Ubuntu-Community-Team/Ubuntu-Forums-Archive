---
title: "Intel HDA Realtek ALC663 Headphones/Headset no sound issue."
date: 2010-12-20
forum: New to Ubuntu
---

### Post by Koanga on 2010-12-20
[SIZE="5"][SOLVED][/SIZE]
After some more research with various keywords, I managed to come to a thread with someone having the same problem. After looking around a little longer, I found the solution in a separate thread.
For those experiencing the same problem, or a similar problem:

1. Go to /etc/modprobe.d
2. Open up the alsa-base.conf (If its read-only, change its privileges) 
3. At the very bottom add this:
```
options snd-hda-intel model=auto
```
4. Save and reboot your system.
NOTE: The model=auto does not always work for some systems. Go [here]("http://ubuntuforums.org/showthread.php?t=314383") for more information 

[SIZE="2"]I've been researching diligently, and I have found next to nothing on this issue I've been facing. Most of the information I have found is dated three or four years ago, or it is irrelevant.

Ever since I have installed 10.04, I have had an issue where speaker sound on my laptop (Asus G51vx-Rx05) works fine, but any headset/headphones plugged into their corresponding jack do not play any sound. After looking at the official sound troubleshooting guide, I have found no solution to my issue. I found that it would be appropriate to post in this section due to being a beginner in Ubuntu/Linux.

Alsamixer:
[IMG]http://i55.tinypic.com/16b0pdu.png[/IMG] 

If you would like me to provide any other information, please do post such a request.[/SIZE]

---

### Post by Hebefrolfing on 2011-03-21
Thank you very much for posting that solution! I had the same problem, and fixed it in under a minute after reading your post. Didn't need to change the file permissions, just opened a terminal and typed this:
sudo gedit /etc/modprobe.d/alsa-base.conf
After adding the code to the bottom, I hit save and rebooted. Went back into alsamixer and unmuted and turned up the headphones then there was sound! Thanks again!

---

### Post by Hebefrolfing on 2011-03-26
Have the same problem now in Arch Linux... any ideas?

---

### Post by AllGamer on 2012-02-14
Thank you very much this fixed the no sound from headphones output problem on the ASUS G60VX with a Realtek ALC663

---

