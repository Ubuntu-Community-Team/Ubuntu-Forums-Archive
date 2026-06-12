---
title: "audio and video errors"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by r.v.the.evil on 2009-08-19
hello everyone to visitors of this forum....
i am suffring from 3 problems
1. good voice clarity ,,, but not as much bass as working on windows
2. laptop internal speakers not working
3. vedio can't be played on full scree ... it usually gives black screen or hangs my lap






plz  give me the solution of any one of them

---

### Post by Aquilastudio.com on 2009-08-19
Could you post the specs and model of your laptop ;)

---

### Post by r.v.the.evil on 2009-08-19
compaq laptop 
amd 64 athlon processor
ati graphic card raedon

---

### Post by r.v.the.evil on 2009-08-19
compaq pressiro cq45
and lspci gives
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by Aquilastudio.com on 2009-08-19
Do you have the model so I could check your specific settings such as speaker drivers and all those goodies?

---

### Post by r.v.the.evil on 2009-08-19
its HP laptop manely known as compaq peserio cq45

---

### Post by r.v.the.evil on 2009-08-19
aplay -l gives
**** List of PLAYBACK Hardware Devices ****
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Aquilastudio.com on 2009-08-19
check this thread out
[http://ubuntuforums.org/showthread.php?t=1163647&highlight=idt+sound](http://ubuntuforums.org/showthread.php?t=1163647&highlight=idt+sound)

---

### Post by r.v.the.evil on 2009-08-19
that seems to be very complicated thread.. can u please explain manually
or u can solve my other two problems

---

### Post by Aquilastudio.com on 2009-08-19
Wat do you mean by good voice clarity?
Fullscreen issues could be caused by hundreds of things. I see that you have Ati. Ati can be a pain in the neck BUT... Try disabeling compiz or any other graphics addons you have and trooubleshoot to se what the problem might be. Ubuntu graphics are very awsome if configured correctly but this is a very large problematic area. For some it works, for others they have to retrace their steps... 
About the sound make sure your volume in the MIXER NOT the regular volume bar is all the way up.
I think I had this problem 2yrs ago because ubuntu installed with the sound muted .

---

### Post by r.v.the.evil on 2009-08-19
well graphics are as fin as in other pc's
i have the drivers and they support 3d acceleration even
but videos are not playing at good quality


clear sound means a songs played in windows wen equalizer is off
but they cant give high beats wich can be changed in winamp and many windows softwares

---

### Post by Aquilastudio.com on 2009-08-19
Get a better media player such as VLC(I love vlc) and try both audio and video...

---

### Post by r.v.the.evil on 2009-08-19
vlc gives the same problem when it is clicked on full screen

u r the same guy in configure wines thread
i also know torrents
u can discuss same issue here after thet

---

### Post by r.v.the.evil on 2009-08-19
[quote=Aquilastudio.com;7812290]Get a better media player such as VLC(I love vlc) and try both audio and video...[/quote

is there any equalizer in any of the ubuntu softwares

---

### Post by Aquilastudio.com on 2009-08-19
oh yes there is.

---

### Post by r.v.the.evil on 2009-08-19
well i got that equilizer in vlc media player
can u please tell me about
how to full screen videos

---

### Post by r.v.the.evil on 2009-08-19
can it be a plugin problem

---

### Post by Aquilastudio.com on 2009-08-19
maybe. The fullscreen is dificult to solve. It might just be abug in the drivers which would stink. I am not in ubuntu rite now so I cant experiment but you could try going to system -> display drivers... and updating

---

### Post by Aquilastudio.com on 2009-08-19
About gaming:
[http://maketecheasier.com/4-ways-to-play-windows-game-on-linux/2008/08/19](http://maketecheasier.com/4-ways-to-play-windows-game-on-linux/2008/08/19)
Cedcega is the one i am familiar with the most.

---

### Post by r.v.the.evil on 2009-08-19
ok i will find its solutuin on net.
so if i want 2 play games on it what should i do
which prefers the most

---

### Post by r.v.the.evil on 2009-08-19
ok i read that from were can i get tht cedcga
or pole

---

### Post by Aquilastudio.com on 2009-08-19
of course you could get it at cedega.com but its not free. I searched cedega torrent on google that should do the trick. Same for the other softwares.

---

### Post by r.v.the.evil on 2009-08-19
r u there

---

### Post by r.v.the.evil on 2009-08-19
r there any special games for linux

---

### Post by Aquilastudio.com on 2009-08-19
ya

---

### Post by Aquilastudio.com on 2009-08-19
go to synaptic and get some fun 3d games. No there are no games like Call of Duty quality specifically for linux srry... Except unreal tournament...

---

### Post by r.v.the.evil on 2009-08-19
ok bye then 
if u get the answers ofplaying video at full screen 
or for laptop speakers please rply to my id

---

### Post by r.v.the.evil on 2009-08-20
any one who can give me solution of how to play video on full screen

---

