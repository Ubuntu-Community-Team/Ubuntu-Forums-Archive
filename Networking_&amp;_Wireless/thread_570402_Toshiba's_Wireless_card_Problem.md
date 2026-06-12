---
title: "Toshiba's Wireless card Problem"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by stalinheredia on 2007-10-08
Hello guys and thanks in advance. Festy (7.04) came with network manager install and its working fine when is connected with a wired connection. However, my wireless card seems not to be detected. what can i do to fix this problem..my laptop is a toshiba sal A215-s4757 and this is my lspci:

lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7917
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791f
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
__________________

---

### Post by guimenez on 2007-10-10
For me its the same (a200). 

my ubuntu can't find the wireless configuration, because its not detecting my card

Please, someone help

Thanks

---

### Post by raiwo on 2007-10-10
connect to wired connection &

```
sudo update-pciids
```

to update id:s

---

### Post by raiwo on 2007-10-10
> **guimenez said:**
> For me its the same (a200). 

my ubuntu can't find the wireless configuration, because its not detecting my card

Please, someone help

Thanks

i think your card is Atheros AR5006EG, use ndiswrapper & windows net5211.inf driver

---

### Post by rustybronco on 2007-10-10
"14:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)"
Or try wicd.
Can you post the model and revision# off the card

---

### Post by blahquaker on 2007-10-11
I got mine working using ndiswrapper with the windows xp driver (you can download it from atheros.cz). 

read this thread:
[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

once it's recognized, wicd is nice for managing the connections.

---

### Post by stalinheredia on 2007-10-11
Thanks A Million Guys, It Worked With The Xp Drivers>>>you Guy Are Wonderful>>>>>>>

---

### Post by crazedgremlin on 2007-10-21
stalinheredia:

I'm considering buying that laptop.  Have you had any problems other than this?  If yes, what are they?

---

### Post by blahquaker on 2007-10-22
mine is a a215-s4807, but it's probably the same thing...

I never got the front headphone and microphone jacks working. I got the headphone jack to output sound at one point, but the speakers didn't shut off when I plugged in the headphones. I lost the headphone sound when I upgraded to gutsy, but since it wasn't working properly I haven't bothered to go through rebuilding alsa again.

The webcam works, but doesn't seem to be recognized by most software... not sure if the microphone in the webcam works or not (don't have a good way to test it).

I've never used any of the card slots, so I can't comment there.

everything else I've been able to get working.

---

### Post by Mrsongs on 2007-10-22
Regarding, at least, the upgrade to Gutsy, I just had a similar problem with my Toshiba A135-S2386 that I managed to resolve. The upgrade went fine, but then things began to deteriorate. When I deactivated the wireless to use a wired Ethernet connection at a hotel, the wireless device vanished. Video issues began to manifest themselves as well. To make a long story short, I activated the restricted drivers manager(System/Administration/Restricted Drivers Manager) and got a message saying it couldn't work unless I downloaded a certain restricted drivers package. I downloaded that package using Synaptic, at which point the Restricted Drivers Manager came up, saying that two drivers listed were not in use. Lo and behold, they were the proprietary ATI graphics driver (maybe on your machine, maybe not) and the proprietary Atheros wireless HAL layer. I clicked on the red radio buttons to "remove" the drivers, then clicked again and got green buttons that indicated that they had been downloaded and installed. The wireless device returned and I configured it normally, and the video stabilized as well. Your mileage may vary, but it's worth checking out.

Regarding the sound, I had a similar problem bringing it up in Feisty, but adding the line

options snd-hda-intel model=6stack-digout

to the file /etc/modprobe.conf brought it up. If you can't find the file /etc/modprobe.conf, create it and insert the line. I can't isolate headphone output from speaker output, but my understanding is that the problem is related to the hardware. I got a good price on my laptop, and Ubuntu brings out the best in it, so I can't complain. :)

---

### Post by Mrsongs on 2007-10-23
> **Mrsongs said:**
> Regarding, at least, the upgrade to Gutsy, I just had a similar problem with my Toshiba A135-S2386 that I managed to resolve. The upgrade went fine, but then things began to deteriorate. When I deactivated the wireless to use a wired Ethernet connection at a hotel, the wireless device vanished. Video issues began to manifest themselves as well. To make a long story short, I activated the restricted drivers manager(System/Administration/Restricted Drivers Manager) and got a message saying it couldn't work unless I downloaded a certain restricted drivers package. I downloaded that package using Synaptic, at which point the Restricted Drivers Manager came up, saying that two drivers listed were not in use. Lo and behold, they were the proprietary ATI graphics driver (maybe on your machine, maybe not) and the proprietary Atheros wireless HAL layer. I clicked on the red radio buttons to "remove" the drivers, then clicked again and got green buttons that indicated that they had been downloaded and installed. The wireless device returned and I configured it normally, and the video stabilized as well. Your mileage may vary, but it's worth checking out.

Regarding the sound, I had a similar problem bringing it up in Feisty, but adding the line

options snd-hda-intel model=6stack-digout

to the file /etc/modprobe.conf brought it up. If you can't find the file /etc/modprobe.conf, create it and insert the line. I can't isolate headphone output from speaker output, but my understanding is that the problem is related to the hardware. I got a good price on my laptop, and Ubuntu brings out the best in it, so I can't complain. :)
Forgot, then remembered when the sound disappeared from the new Gutsy install--compile and install  the latest ALSA drivers  (there will be a HOWTO in the forums) and then

sudo modprobe snd-hda-intel

At that point, there will be a module installed for the line in modprobe.conf to configure...

---

