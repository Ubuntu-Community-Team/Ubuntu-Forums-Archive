---
title: "Ubuntu 8.10/HP Notebook/Intel Card -- Sound Errors"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by happytofu on 2009-02-09
First, I am new, new, new to Ubuntu.  I've been dying to change to Linux for years, and finally had the courage to install it on my new laptop.

However, I'm having a few issues.  First and foremost, I have no sound.  I just hear a do do do do do noise.  I tested my settings and receive this error:

**audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource**

My card is Intel (I don't know anything beyond that) and my computer is an HP Pavilion.  I'm using Ubuntu 8.10.

Also, I cannot figure out the Linux equivalent of CTRL+ALT+DELETE from Windows.  After testing my sound, neither the "X" nor "Close" buttons work; Sound Preferences freezes up and fails to respond.

Please heeeelp me!

And thanks in advance!

---

### Post by greyfox1 on 2009-02-09
Hi Happytofu, welcome to the forums and Ubuntu!  I hope that you are able to stay happy with your choice.

I have two links to share with you:

1. I presume you are using Intrepid Ibex, the latest version of Ubuntu, correct?  Please see [PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578") <== this very useful guide has helped me more than once
2. [A guide to useful keyboard shortcuts in the event of a lockup]("http://www.junauza.com/2009/01/linux-keyboard-shortcuts-to-exit-safely.html")

I hope these help you!!

If you still have problems, you should post what you did and what change(s) you see, if any, after making the changes.  I or someone else will surely be along to help you :D

---

### Post by happytofu on 2009-02-09
I followed the steps, and everything seemed to work fine, but on step 5 it says, *In the Output Devices section you will see a listing of the playback devices available on your system.*

...I'm getting "No Output Devices Available"?

---

### Post by greyfox1 on 2009-02-10
Hmm, that doesn't sound good.  It sounds like the system either hasn't detected or doesn't support your sound card.  Please open a Terminal and type the command:

```
lsusb
```

Then copy & paste the output here.  That should tell us what sound card you have.

You might want to consult [this page]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsIntel") for a list of supported Intel cards.

---

### Post by happytofu on 2009-02-10
C/Ping...:

Bus 008 Device 002: ID 064e:c107 Suyin Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 138a:0001  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Edit:
I followed links to this thread: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) and I'm trying this now.

Edit 2:
Installation of the newer ALSA was successful, but I still get the same errors and am still without sound.  Also, I now have two things installed, I think, ALSA and PulseAudio, so I have no idea if this is relevant or if I should/can uninstall one of them...?

I also found this information, though I don't know if it's helpful:
Codec: IDT 92HD71B7X
Codec: Generic 8086 ID 2802

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by greyfox1 on 2009-02-10
A little background info: ALSA (Advanced Linux Sound Architecture) is an older sound system-- a couple of releases ago, Ubuntu switched over to PulseAudio.  However due to various problems, many people prefer to revert back to ALSA (from what I read, this is because the Ubuntu team did a poor job of implementing PA properly).  Which would be better for you I'm not really sure.  Having both installed shouldn't be a problem, but changing your configuration by following a tutorial for one or another could cause some havoc (sorry I'm no expert with this part of things).

Also, I screwed up with my last post.  The command shouldn't have been lsusb (a command to list USB devices), it should have been lspci (list PCI devices).  Apologies for that.  Could you post the output of lspci please?  I presume you'll see (among other things) something similar to the last few lines of your last post.  The point of this step is to make sure that Linux is seeing your hardware.

---

### Post by happytofu on 2009-02-11
C/Ping...:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
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
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
05:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

---

### Post by greyfox1 on 2009-02-12
Thanks.  It looks like this audio device is known to have some problems in Ubuntu.  [Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424") is the bug report on launchpad (there has been activity there in the last 2 days) and [here]("http://ubuntuforums.org/showpost.php?p=6552654&postcount=14") is a fix somebody says will work.  The poster "kezeb" says to "cd" to the file but what you should really do is issue the command:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

and add the 3 lines he mentions to the end of the file, save, and reboot.  Good luck!

---

### Post by happytofu on 2009-02-14
That worked like a charm.  Thanks so much for your help!

---

### Post by greyfox1 on 2009-02-15
Wahoo!  Glad to hear you're in business.  Enjoy Ubuntu! :D

---

