---
title: "No Audio with Xubuntu 8.10"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by longcipher on 2009-03-10
Hello,

I'm almost there -- I've figured out my wireless and screen resolution issues but cannot get audio with Xubuntu Ibex.

I'm running the software on a Gateway MX3230 laptop.

Any advice would be truly appreciated.

---

### Post by halovivek on 2009-03-10
could you post the output of below one from terminal?
lspci

---

### Post by longcipher on 2009-03-10
Halovivek... thanks for your help, here is the readout from terminal:


00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

---

### Post by longcipher on 2009-03-12
bump...

can anyone help?

---

### Post by longcipher on 2009-03-15
This is the last time I'll bump this -- can anyone help me? Please?

---

### Post by b4n4n4 on 2009-03-16
Maybe [this will help...]("http://ubuntuforums.org/showthread.php?t=1014121")

---

### Post by longcipher on 2009-03-16
> **b4n4n4 said:**
> Maybe [this will help...]("http://ubuntuforums.org/showthread.php?t=1014121")

Thanks -- I used that thread to help me fix my screen resolution issues but the audio interface is different than in Ubuntu so things still aren't working here.

---

### Post by markbuntu on 2009-03-16
Try this. Add this to the end of the /etc/modprobe.d/alsa-base file

options snd-via82xx ac97_quirk

---

### Post by longcipher on 2009-03-16
> **markbuntu said:**
> Try this. Add this to the end of the /etc/modprobe.d/alsa-base file

options snd-via82xx ac97_quirk

Please forgive my ignorance, but I don't know how to access the file that I am supposed to append. I am a super-new Ubuntu/Linux user. Is it possible to give me a little more direction?

Thanks.

---

### Post by halitech on 2009-03-16
try this from a terminal
```
gksu mousepad /etc/modprobe.d/alsa-base
```
then add the line and save the file and reboot

---

### Post by longcipher on 2009-03-16
I did as you said and pasted the line of code at the very end of the file, saved, and rebooted.

and... still nothing.

Before I added the line of code, I could control the master level with my hardware volume wheel - and when I clicked on the speaker icon I was presented with a mixer.

Now, when I click on the speaker icon, I am presented with an empty mixer.

I am open to any other suggestions. :D

---

### Post by halitech on 2009-03-17
I would hazard a guess that it was the wrong code. reopen the file and remove the line of code you entered and reboot again. Then post the output of
```
aplay -l
```

---

### Post by thehouseofho on 2009-03-17
Here's a really good guide.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by longcipher on 2009-03-21
> **halitech said:**
> I would hazard a guess that it was the wrong code. reopen the file and remove the line of code you entered and reboot again. Then post the output of
```
aplay -l
```

Sorry - i was away on business fro the week. Here is the output you requested:

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by starmian on 2009-10-25
I am new to Linux after years of using windows.  Please be patient with me.

I am using Jaunty and have the same machine (Gateway MX3230) and have the same issues after installing.  I have worked through the display issues (that still exist in Jaunty) but had no problems with my wireless.

I have been unable to determine what finally fixed this issue by reading the post.  I have tried all the suggestions that were suggested to the other user with no affect.  My audio still does not work.  

Could someone please help?

---

