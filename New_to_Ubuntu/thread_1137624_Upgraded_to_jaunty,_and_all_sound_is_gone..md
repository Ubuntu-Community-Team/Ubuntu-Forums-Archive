---
title: "Upgraded to jaunty, and all sound is gone."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Timzor on 2009-04-25
I just upgraded to Jaunty Jackalope from Intrepid Ibex, and now I have no sound unless using headphones.
I'm not sure what the relevant info about my computer is, but you can find most of the specs here:
[http://www.bestbuy.com/site/olspage.jsp?skuId=9027714&st=dv3510&lp=1&type=product&cp=1&id=1218010176167](http://www.bestbuy.com/site/olspage.jsp?skuId=9027714&st=dv3510&lp=1&type=product&cp=1&id=1218010176167)

If anyone can help, I would greatly appreciate it.

*edit*
Someone mentioned the link to my specs is dead.  It still works for me, but...
My computer is an HP Pavillion Laptop, model dv3510nr
> 
#
Processor Brand
Intel®
#
Processor Platform
Intel® Centrino® 2
#
Processor
Intel® Core™2 Duo Mobile
#
Processor Speed
2.0GHz
#
Display Type
WXGA high-definition widescreen with LED BrightView technology (1280 x 800)
#
Screen Size
13.3"
#
System Bus
1066MHz
#
Cache Memory
3MB on die level 2
#
System Memory (RAM)
4GB
#
System Memory (RAM) Expandable To
8GB
#
Type of Memory (RAM)
DDR2
#
Hard Drive Type
Serial ATA (5400 rpm)
#
Hard Drive Size
320GB
#
Optical Drive
Double-layer DVD±RW/CD-RW
#
Optical Drive Speeds
Drive speeds not specified
#
Direct-Disc Labeling
No
#
Digital Media Reader or Slots
Yes, digital media card reader
#
Graphics
NVIDIA GeForce 9300 GS
#
Video Memory
512MB (dedicated); up to 2302MB total available graphics memory
#
Personal Video Recorder (PVR)
No
#
TV Tuner
No
#
MPEG
Yes
#
Built-in Webcam
Yes
#
Modem
56 Kbps*
*Capable of receiving 56 Kbps downloads. However, current regulations limit download speed to 53 Kbps.
#
Networking
Built-in 10/100/1000 Gigabit Ethernet LAN (RJ-45 connector)
#
Wireless Networking
Wireless-A+B+G+N
#
Bluetooth-Enabled
Yes
#
Security Technology
Biometric fingerprint reader
#
S-Video Outputs
No
#
Additional Audio/Video Connectors
HDMI
#
Speakers
Built-in Altec Lansing
#
PCMCIA Slots
1 ExpressCard/34
#
USB 2.0 Ports
3
#
IEEE 1394 FireWire Ports
None
#
Parallel Ports
None
#
Serial Ports
None
#
Game Ports
None
#
Laptop Weight
Ultraportable (5.5 lbs. or less)
#
Battery Type
Lithium-ion
#
Battery Life
Up to 4 hours and 15 minutes
#
Pointing Device
Touchpad
#
Operating System
Windows Vista Home Premium 64-bit with SP1
#
Included Software
HP PhotoSmart Essentials, MediaSmart; Microsoft Works; Muvee autoProducer; CyberLink DVD Suite; ProtectSmart Hard Drive Protection; Norton Internet Security 2008 (12 months)
#
Included Accessories
HP mobile remote
#
ENERGY STAR Qualified
Yes

And here is the result of my lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```

---

### Post by spiderbatdad on 2009-04-25
more information might be helpful...regarding your computer specs.

also make sure your sound master and pcm are up in the alsa mixer. Try all the gui tools for sound, etc. If all else fails, you can rebuild alsa with a good tutorial found online...it isnt as hard as it might sound, and you could learn a bit about compiling packages from source. If that all sounds terrible, perhaps try reiinstalling it from synaptic package manager. Sorry your having this problem and good luck.

---

### Post by Crayboff on 2009-04-25
I'm no expert, but I'd first try this stuff:

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

---

### Post by Timzor on 2009-04-25
> **spiderbatdad said:**
> more information might be helpful...regarding your computer specs.

also make sure your sound master and pcm are up in the alsa mixer. Try all the gui tools for sound, etc. If all else fails, you can rebuild alsa with a good tutorial found online...it isnt as hard as it might sound, and you could learn a bit about compiling packages from source. If that all sounds terrible, perhaps try reiinstalling it from synaptic package manager. Sorry your having this problem and good luck.

Here are my computer specs.
[http://www.bestbuy.com/site/olspage.jsp?skuId=9027714&st=dv3510&lp=1&type=product&cp=1&id=1218010176167](http://www.bestbuy.com/site/olspage.jsp?skuId=9027714&st=dv3510&lp=1&type=product&cp=1&id=1218010176167)

I tried reinstalling alsa from the synaptic package manager, but it did not work.  If you would link me to that tutorial you mentioned, I can try rebuilding it like you mentioned.

> **Crayboff said:**
> I'm no expert, but I'd first try this stuff:

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)
Okay, I followed all the instructions on that page, and still no sound.  I was interested in this part:
"2) If you have HP 6730s and was only getting sound from the headphone jack, not the internal speakers use the following solutions"
Because I have an HP computer, and sure enough, when I plugged my headphones in, I was getting sound.  However, I followed those instructions as well, with no results.

I also followed the link to this page
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

And followed the instructions there, as well.  Still no sound.

---

### Post by pspsampsp on 2009-04-25
go system -> prefernces -> sound and try changing the options in there to alsa or different other options

---

### Post by Timzor on 2009-04-25
> **pspsampsp said:**
> go system -> prefernces -> sound and try changing the options in there to alsa or different other options

Tried all of them (Via the test button).  Nothing worked.

---

### Post by Timzor on 2009-04-25
Bump

---

### Post by Timzor on 2009-04-26
bump

---

### Post by grep65535 on 2009-04-26
same issue here, wondering if there's some solid universal way to fix this.
Sound has worked on here every version since 6.04, now 9.04 and no sound.

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

Edit: my wife had my speakers turned off  >X(

---

### Post by Timzor on 2009-04-26
> **grep65535 said:**
> same issue here, wondering if there's some solid universal way to fix this.
Sound has worked on here every version since 6.04, now 9.04 and no sound.

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

Good to see I'm not suffering alone... probably increases the chance that a fix will be found.

---

### Post by Timzor on 2009-04-26
bump

---

### Post by waspbr on 2009-04-26
hmmm, the link to your specs seems dead now. Thought it seems that you have a HP desktop and I would expect that to work out of the box. if I had your problem then I would try a few things


1-update you system
2- pop in a liveCD of Jaunty, see if the sound works there (System>Preferennces>Sound).
3- post your specs again and post the result of you lspci

---

### Post by spiderbatdad on 2009-04-26
kk Timzor, to rebuild alsa:
download the latest driver here:[http://alsa-project.org/main/index.php/Main_Page](http://alsa-project.org/main/index.php/Main_Page)
Next make sure you have build-essential...the tools for compiling source code. ```
sudo apt-get install build-essential linux-headers-$(uname -r)

```Then untar the alsa package by right click and select extract here...we'll assume the package is on your desktop. cd into the alsa folder```
cd Desktop/alsa...
```use the tab key to auto complete folder names. Once in the alsa directory, ```
./configure --with-cards=all

make
sudo make install
```next edit /etc/modprobe.d/options, add the following line: ```
options snd-hda-intel model=laptop enable=1 index=0
```You may have add the same line to alsa-base in the other tutorial. thats ok. Add the following to /etc/modules; ```
snd-hda-intel
```
Reboot your system. hopefully you have sound...you may need to check volume controls again...master and pcm.
If you still have no sound, ```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
sudo alsa force-unload
sudo depmod -ae
sudo modprobe snd-hda-intel
```Restart again. Good luck.

---

### Post by linux_tech on 2009-04-26
You can also try re-installing alsa sound base. To do this in terminal-
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
reboot and test

---

### Post by Stewtheking on 2009-04-30
> **Crayboff said:**
> I'm no expert, but I'd first try this stuff:

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

Worked for me. Thanks!

---

### Post by Timzor on 2009-05-08
All right, I want to thank everyone for their help so far, and apologize for abandoning the thread.  Exam week snuck up on me, and before I knew it my computer's sound was the least of my worries.

> **waspbr said:**
> hmmm, the link to your specs seems dead now. Thought it seems that you have a HP desktop and I would expect that to work out of the box. if I had your problem then I would try a few things


1-update you system
2- pop in a liveCD of Jaunty, see if the sound works there (System>Preferennces>Sound).
3- post your specs again and post the result of you lspci
1.  Updated multiple times.  Still no good.
2.  Unfortunately, no.  I was really hoping it would, but even booting from CD I get no sound.
3.  My computer is an dv3510nr.  The link to the specs still works for me, but just in case:
> 
#
Processor Brand
Intel®
#
Processor Platform
Intel® Centrino® 2
#
Processor
Intel® Core™2 Duo Mobile
#
Processor Speed
2.0GHz
#
Display Type
WXGA high-definition widescreen with LED BrightView technology (1280 x 800)
#
Screen Size
13.3"
#
System Bus
1066MHz
#
Cache Memory
3MB on die level 2
#
System Memory (RAM)
4GB
#
System Memory (RAM) Expandable To
8GB
#
Type of Memory (RAM)
DDR2
#
Hard Drive Type
Serial ATA (5400 rpm)
#
Hard Drive Size
320GB
#
Optical Drive
Double-layer DVD±RW/CD-RW
#
Optical Drive Speeds
Drive speeds not specified
#
Direct-Disc Labeling
No
#
Digital Media Reader or Slots
Yes, digital media card reader
#
Graphics
NVIDIA GeForce 9300 GS
#
Video Memory
512MB (dedicated); up to 2302MB total available graphics memory
#
Personal Video Recorder (PVR)
No
#
TV Tuner
No
#
MPEG
Yes
#
Built-in Webcam
Yes
#
Modem
56 Kbps*
*Capable of receiving 56 Kbps downloads. However, current regulations limit download speed to 53 Kbps.
#
Networking
Built-in 10/100/1000 Gigabit Ethernet LAN (RJ-45 connector)
#
Wireless Networking
Wireless-A+B+G+N
#
Bluetooth-Enabled
Yes
#
Security Technology
Biometric fingerprint reader
#
S-Video Outputs
No
#
Additional Audio/Video Connectors
HDMI
#
Speakers
Built-in Altec Lansing
#
PCMCIA Slots
1 ExpressCard/34
#
USB 2.0 Ports
3
#
IEEE 1394 FireWire Ports
None
#
Parallel Ports
None
#
Serial Ports
None
#
Game Ports
None
#
Laptop Weight
Ultraportable (5.5 lbs. or less)
#
Battery Type
Lithium-ion
#
Battery Life
Up to 4 hours and 15 minutes
#
Pointing Device
Touchpad
#
Operating System
Windows Vista Home Premium 64-bit with SP1
#
Included Software
HP PhotoSmart Essentials, MediaSmart; Microsoft Works; Muvee autoProducer; CyberLink DVD Suite; ProtectSmart Hard Drive Protection; Norton Internet Security 2008 (12 months)
#
Included Accessories
HP mobile remote
#
ENERGY STAR Qualified
Yes

And here is the result of my lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```

---

### Post by Timzor on 2009-05-08
> **spiderbatdad said:**
> kk Timzor, to rebuild alsa:
download the latest driver here:[http://alsa-project.org/main/index.php/Main_Page](http://alsa-project.org/main/index.php/Main_Page)
Next make sure you have build-essential...the tools for compiling source code. ```
sudo apt-get install build-essential linux-headers-$(uname -r)

```Then untar the alsa package by right click and select extract here...we'll assume the package is on your desktop. cd into the alsa folder```
cd Desktop/alsa...
```use the tab key to auto complete folder names. Once in the alsa directory, ```
./configure --with-cards=all

make
sudo make install
```next edit /etc/modprobe.d/options, add the following line: ```
options snd-hda-intel model=laptop enable=1 index=0
```You may have add the same line to alsa-base in the other tutorial. thats ok. Add the following to /etc/modules; ```
snd-hda-intel
```
Reboot your system. hopefully you have sound...you may need to check volume controls again...master and pcm.
If you still have no sound, ```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
sudo alsa force-unload
sudo depmod -ae
sudo modprobe snd-hda-intel
```Restart again. Good luck.

I followed your instructions until you told me to "edit /etc/modprobe.d/options, add the following line: options snd-hda-intel model=laptop enable=1 index=0"
I wasn't sure how to do that.

> **linux_tech said:**
> You can also try re-installing alsa sound base. To do this in terminal-
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
reboot and test
I tried this as well.  Still no sound.

---

### Post by spiderbatdad on 2009-05-08
if you are running jaunty, /etc/modprobe.d/options is gone. instead try putting the options in /etc/modprobe.d/alsa-base.conf

---

### Post by kansasnoob on 2009-05-08
First follow **only** the Basic Troubleshooting steps here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Then look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Notice where it says: **Note 1. Jaunty users: If you are upgrading from Hardy or Intrepid, it is highly recommended that you follow the guide to remove obsolete configuration. If you have performed a clean installation, follow the guide only if you are experiencing issues.**

And then: **Jaunty users: Follow Part A.**

---

### Post by Timzor on 2009-05-08
> **spiderbatdad said:**
> if you are running jaunty, /etc/modprobe.d/options is gone. instead try putting the options in /etc/modprobe.d/alsa-base.conf

I'm sorry, but I just don't understand what you're asking me to do.

> **kansasnoob said:**
> First follow **only** the Basic Troubleshooting steps here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Then look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Notice where it says: **Note 1. Jaunty users: If you are upgrading from Hardy or Intrepid, it is highly recommended that you follow the guide to remove obsolete configuration. If you have performed a clean installation, follow the guide only if you are experiencing issues.**

And then: **Jaunty users: Follow Part A.**

Okay... apparently my sound card is not supported.  It's an Intel Corporation 82801I (ICH9 Family) HD Audio Controller, and I didn't see it listed.
Am I just sunk, then?

Additionally, when I continued trying to follow the instructions, I got to this part:
> Now take a look at ALSA-Configuration.txt again, and you will find a section that looks like this, which matches up with my soundcards codec: 
I couldn't find my codec on the web page (Codec: IDT 92HD71B7X)
So, I couldn't really go any further.

Also, on the second page you provided, following the first step
> 1. Backup (and then delete) your previous configuration files:
Results in
```
bash: $: command not found
```
Should I proceed anyway?

---

### Post by small3265 on 2009-09-09
I'm having the exact same problem. I've been looking all over for a solution with no joy. I beg you for a fix so I don't have to resort back to Vista. Maybe just downgrade to a past version of Ubuntu until this issue is solved.

---

