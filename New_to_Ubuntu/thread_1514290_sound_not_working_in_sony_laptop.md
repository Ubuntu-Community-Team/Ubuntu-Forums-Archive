---
title: "sound not working in sony laptop"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by bhavya juneja on 2010-06-20
[SIZE=2]hi..
m just a beginner and statrted ubuntu 10.04 two days earlier...everything seems great except that sound is not working in my sony laptop...i also have windows 7 in which my sound works..
I have tried installing driver from [/SIZE]
**[SIZE=2]system > administration > hardware drivers[/SIZE]**

and have also tried 
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]sudo apt-get install linux-backports-modules-alsa-2.6.32-21-generic[/FONT][/FONT][/COLOR]
its still not working.
can anyone help??

---

### Post by salefish on 2010-06-20
I found this post which helped me get my audio working quickly. [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound")
Where he says shell read it as terminal.

---

### Post by lkjoel on 2010-06-21
Go to this website [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

---

### Post by bhavya juneja on 2010-06-23
thanks salefish but following that procedure i could not find driver for my card..
when i type 

aplay -l

in terminal
the output is


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and i could not find ways for installing drivers for it...rather i am not sure if there are available too.

---

