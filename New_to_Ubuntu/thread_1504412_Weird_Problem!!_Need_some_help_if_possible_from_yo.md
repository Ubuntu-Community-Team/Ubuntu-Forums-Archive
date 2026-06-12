---
title: "Weird Problem!! Need some help if possible from you pro's :)"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by ibe2fly4chu on 2010-06-08
Recently i installed ubuntu 10.4. Everything was working great except i have this little problem.
i) Problem: Whenever i go to system>administrator>Hardware drivers, and install one of the 2 graphic card driver ubuntu recommends, it installs perfectly fine. However upon rebooting...the sound will on the computer will stop working completely. If i then go back and uninstall the any of the 2 graphic card drivers, and reboot, the sound comes back and works fine.

ii) What i would like to accomplish: Well its kinda evident that i want both sound and my graphic card drivers to be active. I would really like to have desktop effects enabled AND be able to listen music and watch videos etc.

iii) Hardware information: a) card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
b) The exact graphic card i am using is the Nvidia Gforce 9400GT.



c) The Motherboard i am using is "Nforce570 slit-A v5.1". This mother board has a build in sound card, and i have confirmed it to be enabled in the bios. 

UPDATE: oh i'm sorry. Was trying to give all the information i forgot the most common. I am currently on ubuntu 10.4
Any help if any, is greatly appreciated. Thanks in Advance^^

---

### Post by Drenriza on 2010-06-08
what version of ubuntu are you using?

---

### Post by -humanaut- on 2010-06-08
type lspci in a terminal and post it back here

---

### Post by ibe2fly4chu on 2010-06-08
This is the output of the command you suggested:

00:00.0 Host bridge: nVidia Corporation Device 0071 (rev a3)
00:00.1 RAM memory: nVidia Corporation Device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:06.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:07.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

---

### Post by ibe2fly4chu on 2010-06-08
Think its the drivers or the card?

---

### Post by ibe2fly4chu on 2010-06-08
*bump*

---

### Post by sandyd on 2010-06-08
> **ibe2fly4chu said:**
> This is the output of the command you suggested:

00:00.0 Host bridge: nVidia Corporation Device 0071 (rev a3)
00:00.1 RAM memory: nVidia Corporation Device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:06.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:07.0 PCI bridge: nVidia Corporation Device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
**00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)**
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
run
```

gksudo gedit /etc/modprobe.d/alsa-base.conf

```stick this on a new line at the end of a file, save and reboot
```

ptions snd-hda-intel model=3stack

```

---

### Post by ibe2fly4chu on 2010-06-08
i copied both code and did as instructed. then i proceeded to reactivate the graphic card driver. After rebooting however i still have no sound. I removed the graphic card driver and rebooted and the sound returned. One odd thing though, was when i opened that file using the command you gave me, you said to "stick it in a new line"..however there was no other scripts written in that document. It appeared blank...not sure if that changes anything..

---

### Post by sandyd on 2010-06-08
> **ibe2fly4chu said:**
> i copied both code and did as instructed. then i proceeded to reactivate the graphic card driver. After rebooting however i still have no sound. I removed the graphic card driver and rebooted and the sound returned. One odd thing though, was when i opened that file using the command you gave me, you said to "stick it in a new line"..however there was no other scripts written in that document. It appeared blank...not sure if that changes anything..
Fixed the typo.

Gotta refrain from posting and playing Battlefield at the same time ;)

---

### Post by ibe2fly4chu on 2010-06-08
lol no problem in regard to the type o :). I re-did the steps with the correct command and then i reactivated my graphic card drivers and rebooted. Still no sound however T.T

---

### Post by ibe2fly4chu on 2010-06-09
bump

---

### Post by ibe2fly4chu on 2010-06-09
No one has a solution to this??

---

### Post by ibe2fly4chu on 2010-06-09
siiiggghhhh. bump lol

---

### Post by ibe2fly4chu on 2010-06-09
Through various testing i have confirmed that if i switch the hdmi cable to vga that is going from the video card to my monitor, i get perfect sound while having my video card drivers installed. So now the new question is how can i get the sound to work with hdmi. All the threads i found so far refer to different hardware...and none of the solutions provided there worked for me. For now i am switching back to vga, but the quality drop is very noticeable. Does anyone know how to get the hdmi sound working ?

---

### Post by ibe2fly4chu on 2010-06-11
bump

---

