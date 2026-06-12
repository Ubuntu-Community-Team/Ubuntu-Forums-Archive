---
title: "First Linux Build"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by brentk on 2009-03-12
On Monday I got all the parts for a new build. I've tried out both ubuntu and kubuntu before but never really been able to get them to work with my laptop. This is a desktop/htpc build. Everything seems to be compatible, but I'm still having a sound issue and have a couple other questions.

I have both onboard sound (HDA ATI SB VT1708B) and a Creative Xmod. Onboard sound is way quiet, but that's mostly a non issue because I'd rather use my xmod. The problem with that is a few programs are still trying to use the onboard sound. Specifically VLC and XBMC. Both are set to use 'default' sound device. System sounds, Amarok and Dragon player all work fine. I have added the line 'options snd_usb_audio index=0' to alsa-base.

My other questions are probably rather simple. 

Is there a way to launch multiple applications together? Specifically Prism for GMail, Reader, Docs, and Calendar? 

Also, is there a way to load external drives on startup? They're formatted FAT32 and before any program can use them I have to open Dolphin and select each drive. 

Thanks!
Brent

---

### Post by brentk on 2009-03-12
Please?

---

### Post by blueridgedog on 2009-03-12
I suggest you disable the onboard sound in the bios.

Your external drives should mount on boot, if not, boot and post the output of 

```
sudo fdisk -l
```

and 

```
lsusb
```

You can launch many applications with a single command by creating a file with the commands you want to launch:

```
#!/bin/bash
nautilus
firefox
```

Save the file as "launch.sh" or some other name that suits you, then make it executable with
```

chmod u+x launch.sh
```

If you save it on your desktop, you can run it by double clicking it, or you can run it from the terminal with the command

launch.sh

(or whatever you named it)

---

### Post by mrbiggbrain on 2009-03-12
> **brentk said:**
> On Monday I got all the parts for a new build. I've tried out both ubuntu and kubuntu before but never really been able to get them to work with my laptop. This is a desktop/htpc build. Everything seems to be compatible, but I'm still having a sound issue and have a couple other questions.

I have both onboard sound (HDA ATI SB VT1708B) and a Creative Xmod. Onboard sound is way quiet, but that's mostly a non issue because I'd rather use my xmod. The problem with that is a few programs are still trying to use the onboard sound. Specifically VLC and XBMC. Both are set to use 'default' sound device. System sounds, Amarok and Dragon player all work fine. I have added the line 'options snd_usb_audio index=0' to alsa-base.

My other questions are probably rather simple. 

Is there a way to launch multiple applications together? Specifically Prism for GMail, Reader, Docs, and Calendar? 

Also, is there a way to load external drives on startup? They're formatted FAT32 and before any program can use them I have to open Dolphin and select each drive. 

Thanks!
Brent

edit /etc/fstab there should be a few lines, edit one to look like them, but with the mountpoint you want, and the location (ex. sda1, hda1, ect ect)
sda1 is the first drive, first partition.
sda2 is first drive second partition
sdb1 is second drive, first partition

---

### Post by brentk on 2009-03-13
I disabled onboard sound in BIOS. I should have thought of that in the first place so thank you! This successfully stopped sound from playing from the onboard sound, but VLC and XBMC still do not play through the xmod (or at all now). Multimedia systems settings does show  a second digital xmod device that doesn't output the test sound, but cannot be deleted.

---

### Post by brentk on 2009-03-14
Here's the result from aplay -l. I assume what I need is to get card 1 to be card 0, and card 0 to be nothing. I've disabled everything I could in BIOS. The sound device is part of the video chipset to supply sound over HDMI. Of course this board has no hdmi input so having it is stupid, pointless and causing me a ton of frustration. I sort of expected adding the line options snd-hda-hdmi index=-2 or options hda-hdmi index=-2 to alsa-base would fix this but hasn't. Is there some other ID I need or something else I have to fix?


```
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Xmod [Creative Xmod], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by blueridgedog on 2009-03-14
I am not a sound expert, but suggest you port you last posting in the multimedia forum or the hardware forum.

---

