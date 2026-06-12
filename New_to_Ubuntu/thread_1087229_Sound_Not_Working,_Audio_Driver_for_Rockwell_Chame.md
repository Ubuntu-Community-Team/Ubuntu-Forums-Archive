---
title: "Sound Not Working, Audio Driver for Rockwell Chameleon Combo Card"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by noobuntu7 on 2009-03-04
I installed Xubuntu 8.04 (Hardy) on an [HP Pavillion 6653C Desktop PC]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph05437&lc=en&dlc=en&cc=us&lang=en&product=58802"). The installation was quick and easy, so far I haven't had any noticeable bugs. However, the audio isn't working on the PC, I've been trying for a while to fix it.

The soundcard is the [Rockwell Chameleon Combo Card]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07115&lc=en&dlc=en&cc=us&lang=en&product=58802") with an AMC97 Controller. As far as I can tell, Xubuntu doesn't natively support this soundcard. I've tried looking for the drivers online (Yes, I did check the ALSA project web site), but I can't find one.

When I open a terminal and type: *lspci -v* I get:

```
01:09.0 Multimedia audio controller: Rockwell International Unknown device 4310
	Subsystem: Risq Modular Systems, Inc. Unknown device 4310
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 2400 [size=64]
	Capabilities: <access denied>

```

I'm hoping someone can help me with this. Thanks!

---

### Post by dbbolton on 2009-03-04
Try the instructions listed out on this page: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

It may seem tedious, but it has helped me to get the sound going on a few pesky machines.

---

### Post by noobuntu7 on 2009-03-06
Well, I got an unexpected fix :). I tried all of the suggestions in the Sound Troubleshooting guide, but none worked. 

The HP 6653C **had** 128mb of RAM. I wanted to speed it up just a little, and I had an old HP XL753 with 64mb of RAM which I could take out. I popped it out of the XL753 and put it in the 6653C. Rebooted the computer and, voila. The sound worked. I don't know why it worked, but it did and I'm happy.

---

### Post by Jaguarandine on 2009-04-04
I have the exact same problem in Ubuntu, using the same soundcard as the original poster. This card seems to be particularly nasty as I have not found a fix for it in the year and a half that I've been running Ubuntu (I'm now using 8.04). It's been extremely frustrating and has forced me to dual-boot with Windows 2000. 

One thing I've noticed is that under System->Preferences->Sound, it used to show something under the "Device" field. Now, that field is blank. I've installed so may things to try and fix this sound issue (OSS, linuxant files, etc.) that I've probably messed up my orignal settings. I'm still a Linux newb unfortunetly. 

Are there any solutions to this problem? Should I hope for a fix in 9.04? I've spent so much time on this that I'd like to see it through. Thanks for your help :)

---

### Post by Jaguarandine on 2009-04-13
Hi, I posted the above a while ago. My system is a [[COLOR="Blue"]HP Pavilion 8760c desktop[/COLOR]]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph05813&cc=us&lc=en&dlc=en&product=59299") running the same Rockwell Chameleon Combo Card as the OP. I've made significant changes to my system since the last time I replied:

[LIST=1]
[*] I updated the BIOS to 2.02 (latest version). 

[*] Reverted ALSA drivers to the Ubuntu defaults using the "Refreshing/Reinstalling the drivers" section of the [[COLOR="Blue"]SoundTroubeshooting[/COLOR]]("https://help.ubuntu.com/community/SoundTroubleshooting?action=fullsearch&context=180&value=linkto%3A%22SoundTroubleshooting%22") guide. I then manually loaded the riptide module using ```
sudo modprobe snd-riptide
``` as per the guide's instructions.

[*] Installed new version of ALSA via the [[COLOR="Blue"]ALSA upgrade Script[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810").

[*] I upgraded the memory from 256MB to 1.1GB of RAM. Alas, I did not get the OP's magical results, and I still have no sound.
[/LIST]

Here's my system info:
```
marcus@marcus-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:04.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0b.0 Multimedia audio controller: Rockwell International Unknown device 4310
00:0b.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
00:0b.2 Input device controller: Rockwell International Unknown device 4312
00:0c.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
marcus@marcus-desktop:~$ lsusb
Bus 001 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  
marcus@marcus-desktop:~$ cat /proc/asound/cards
 0 [Riptide        ]: RIPTIDE - Riptide
                      Riptide at 0xb800, irq 11 mpu 0x330 opl3 0x388 gameport 0x200
marcus@marcus-desktop:~$ cat /proc/asound/modules
 0 snd_riptide
marcus@marcus-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Riptide [Riptide], device 0: RIPTIDE [RIPTIDE]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
marcus@marcus-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Riptide [Riptide], device 0: RIPTIDE [RIPTIDE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
marcus@marcus-desktop:~$ 


```

At this point I'm seriously thinking about switching to a better supported sound card. I've spent countless hours on this with much frustration and no results. The only thing keeping me from removing the sound card and smashing it to bits is that this experience may benefit other users and maybe the ALSA project. So, does anyone have any suggestions? I appreciate any help you can give. Thanks! ;)

---

