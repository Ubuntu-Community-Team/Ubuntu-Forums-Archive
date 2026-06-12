---
title: "how to update ALSA"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Deadlyhydra on 2009-12-07
Foreword - I am a total noob.
I have searched on the forums and noticed that there are a few articles that mention that the cause of some sound issues like the one i am experiencing can be due to an outdated version of ALSA. Tried to read through the instructions on how to update the software, but i'm more puzzled than ever?

---

### Post by VCoolio on 2009-12-07
Here's what I used two weeks ago. It takes some time for the script to complete, but it works. Don't be alarmed by your terminal cursor turning around like nothing will ever happen.
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by Deadlyhydra on 2009-12-07
that is what i was reading, but doesn't make any sense. to give you an example it says 
Short Alsa-Upgrade script install instructions:
1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.21-3.tar
4. sudo ./AlsaUpgrade-1.0.21-4.sh -di
5. sudo shutdown -r 0

where is the script?

---

### Post by snowpine on 2009-12-07
> **Deadlyhydra said:**
> Foreword - I am a total noob.
I have searched on the forums and noticed that there are a few articles that mention that the cause of some sound issues like the one i am experiencing can be due to an outdated version of ALSA. Tried to read through the instructions on how to update the software, but i'm more puzzled than ever?

Hi there, welcome to the forums! Here is some noob advice: ALSA is updated (along with everything else) through the normal Ubuntu update process.

You can use System->Administration->Update Manager or the terminal commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Stick with these approved methods, and you will have a nice, stable Ubuntu system. :)

I would love to help you with the sound issue, but I have no idea about your hardware. The terminal command:

```
lspci
```

will tell you all about your hardware, including your audio card. (For example, mine is an Intel Corporation 82801G). You can use this information to search these forums for specific answers. Good luck!

---

### Post by Savicava on 2011-07-16
Please help me fix microphone problem! 
My voice comes with the scratchy sound.
It works fine with Windows XP and Windows 7.
I'm using ASUS X59SR.
Here is the info from " lspci " command

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

