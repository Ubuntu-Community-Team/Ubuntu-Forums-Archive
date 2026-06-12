---
title: "sound problem: sound recording / entry problem"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Pavel_Petrovich on 2011-07-27
Just installed ubuntu 10 on a **Sony Vaio laptop**. everything works fine except the **sound entry /recording **part. I am not trying to do anything fancy just trying to make sound entry in Skype and Audacity work. but to no avail....

am using a simple headset, and I **can hear myself talking** through the headset when I am testing skype or audacity, so that would suggest that on the level of sound card all is ok and the headset is functioning. but still there is no way i can get the sound entry to be detected by audacity or skype.

I have tried all the advice and steps i could find on the skype linux support site including downgrading to 2.1 but it did not help and since I am having the same issue in audacity it is probably something else. Naturally i tried all combinations of settings in preferences for audacity as well...

I have been spending 5 hours now on this and it is driving me crazy. 

I have also followed all the typical steps I could find on the forums. (like configuring the alsamixer) 

On the way I have also lost the system-preferences-sound option in my interface and can't get it back using the edit menu, that is i don't know what command to use when adding the menu item. no idea where it went in the first place...

Thanks for helping me out, that's Great! This is my very first post...

---

### Post by sirgogo on 2011-07-27
First off, welcome to the forums. Can't really tell where you are in debugging, so try this;

Open a terminal window and run
```
gnome-volume-control
```

and tinker with it.

If this doesn't work, do this in the terminal:
```
arecord test.wav
```
This should record a wave file to the directory your terminal is open in. To find the current directory, do a 
```
pwd
``` in the terminal.


Now, I've done my fair share share of tinkering with config files and manually grabbing and installing drivers, but [here's ]("https://help.ubuntu.com/community/AudioCapture")where I got this info. Ubuntu wiki's and documentation are sometimes out of date, but still useful.

---

### Post by Pavel_Petrovich on 2011-07-28
Sirgogo,

thank you for this quick response. here's what I got so far:
Open a terminal window and run
     Code:
     gnome-volume-control 
[B][SIZE=1]RESULT: this indeed gives me a sound panel on which everything looks OK, all the recording volumes are UP, except one called "Beep". Sound entry in skype or audacity is still zero...[/SIZE]

[/B] 
If this doesn't work, do this in the terminal:
     Code:
     arecord test.wav 
This should record a wave file to the directory your terminal is open in. To find the current directory, do a 
     Code:
     pwd 
 in the terminal.

**TEST RESULT: did this and the file was created, however no sound was recorded... **

Don't know what is happening, but for one thing when I try to select the sound device for skype or audacity, it only gives me the option: HD Intel (the soundcard on my Sony Vaio laptop I suppose) or 'default'

At the same time, when I am speaking for the test I can hear myself over the headset, which suggests that the headset is recognized, also sound playing over the headset has no issue.

any other ideas?

Pavel_Petrovich

---

### Post by sirgogo on 2011-07-28
Hmm, what sound card are you using? If its a pci card, do a lspci in the terminal to see all pci devices.

It's kinda hard to diagnose remotely, but you can refer to this: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) . Scroll down to the Extra Hints section.

---

### Post by Pavel_Petrovich on 2011-07-30
Hi Sirgogo,

My Quest for Sound continues...

so far the problem was happening when using a traditional headset (not usb but plugged into the two channels of mic and speaker) this did not work so far, So I tried using a USB headset, that works but the sound of the microphone is very feeble somehow, to feeble to use it on skype... so now I am back on the traditinal head set and intent on getting it to work finally.

My soundcard is called 'HDA Intel' and I did the 'lspci' in the terminal (with the headset plugged) here's what it came up with . I have no idea what it means...

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 13)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

I have checked the reading material you recommended, but so far I have not find anything that works in my case

looking forward to any other advice you may have...

Pavel Petrovich

---

### Post by Pavel_Petrovich on 2011-07-30
x

---

### Post by Pavel_Petrovich on 2011-07-31
Hi Sirgogo
Quest for Sound Accomplished...
It took me a lot of time, and I learnt a lot along the way but finally the microphone is working on my Sony Vaio laptop!

thanks to following your link about 'sound hda intel how to' i managed to know which card my Vaio is using:
ALC262
when I do 
/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

the only sony computer registered is:
sony-assamd    Sony ASSAMD

So naturally I tried this one, it did not work. But since by then I had so much more information I was able to search better and I found this thread
[B][http://ubuntuforums.org/showthread.php?t=1515440](http://ubuntuforums.org/showthread.php?t=1515440)
[/B]which speaks exactly about the problem I have been having with my Sony Vaio, and Magic Neophyte explains exactly what one should do.
Roughly you have to say your computer is a particular model of toshiba and not sony or vaio... and then everything will work wonderfully.

Thanks again!

Pavel Petrovich

---

