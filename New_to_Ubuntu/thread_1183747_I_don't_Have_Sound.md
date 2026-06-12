---
title: "I don't Have Sound"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by sidewinderam9m on 2009-06-10
I am new to linux and ubuntu.  Apparently they have problems running creative labs sound blaster x-fi.  I have no sound.  I found a driver on the creative labs website, but don't no how to install it.  Readme says:

In terminal,
 
1) Goto source directory 
2) Execute make command as root 
   make 
   make install

Could someone show me how to write the commands to do this and explain it?

---

### Post by halitech on 2009-06-10
before you try installing the drivers from the web, can you post the output of
```
lspci
```and ```
aplay -l
```

you would do this is the terminal

---

### Post by Person_1873 on 2009-06-10
in order to do the commands the readme tells you, you will need to get into the terminal, the easiest way to do this is to  press alt+F2 and type ```
gnome-terminal
``` you then need to navigate through the directories until you reach your driver source directory, once there you will need to type ```
make
sudo make install
```

---

### Post by sidewinderam9m on 2009-06-10
garrett@garrett-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a4)
00:0e.2 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a5)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
02:05.0 Audio device: Creative Labs SB X-Fi
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
garrett@garrett-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
garrett@garrett-desktop:~$ ls
Desktop           Music     Templates
Documents         Pictures  Videos
examples.desktop  Public    XFiDrv_Linux_Public_US_1.00.tar.gz
garrett@garrett-desktop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
garrett@garrett-desktop:~$

---

### Post by halitech on 2009-06-10
okay, it is seeing both sound cards in your system
[color="red"]00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)[/color]
and
[color="red"]02:05.0 Audio device: Creative Labs SB X-Fi[/color]

it's also seeing the onboard sound as working properly now but I'm guessing you have the speakers plugged into the SB card.

As far as installing the downloaded drivers, you need to extract them first
```
tar -xvf XFiDrv_Linux_Public_US_1.00.tar.gz
```
then
```
cd XFiDrv_Linux_Public_US_1.00
```
then do the make, sudo make install

---

### Post by sidewinderam9m on 2009-06-10
I still have no sound, thanks for your help though.  I ran vista to make sure it worked and it does.  Checked that it wasn't muted.  Been playing with sound preferences but nothing helps.  Any other suggestions?

---

### Post by LowSky on 2009-06-10
dont forget to reboot when completed for new settings to take effect

---

### Post by sidewinderam9m on 2009-06-10
I tried that too.  Still no sounds of any kind.

---

### Post by Bigtime_Scrub on 2009-06-10
Might I suggest a slightly different approach...

I don't know if this will do it for you but it may be worth a shot.

```
 sudo killall pulseaudio
```
```
sudo alsa force-reload
```

After that go to  System>Preferences>Sound and change everything to ALSA

Then after you do that go into terminal and run
```
 alsaconf
```

and then 

```
alsamixer
```

Then try sound.

---

### Post by sidewinderam9m on 2009-06-10
No luck, thanks tho.

---

