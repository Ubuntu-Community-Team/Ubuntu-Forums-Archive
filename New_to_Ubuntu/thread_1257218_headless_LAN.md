---
title: "headless LAN?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by chitowner2 on 2009-09-03
OK, I'm a newbie, especially on this issue so I don't know any jargon or buzzwords for my "problem" so I am just going to describe the scenario and what I'm seeking help to accomplish.

DETAILS
I have jaunty/kde3,5 running on my "desktop" PC. I recently built a new box for multimedia; let's call that one "media". It is running jaunty/kde4.2. I have a ViewSonic N3000w that I want to connect to media by DVI. The mobo in media is an EVGA nForce 730a MB 8200 GPU w/ AM2 CPU and 8G DDR2. I have a Buffalo AirStation WHR300N router and a Buffalo Wireless-N USB2 adapter plugged into media. I also have an Adesso wireless trackball keyboard with a USB dongle plugged into media. So that's the new setup; as you can see (hopefully) I did my homework.

SCENARIO
So I start with everything off, connect the DVI cable from media to the panel and turn them both on. I am expecting two basic things: 1- the display will come up and show me the boot process on media and eventually a desktop, and 2- i expect the wireless devices to automagically connect so that I can share files between desktop and media. 

Here's what I get: no display function. Panel works fine in TV mode, but i get no DVI. The ViewSonic has a native 720p and the DVI must be toggled in the panel's OSD setup; it cannot be clicked from the remote. I emailed ViewSonic and they basically tell me to do what I've already done.

SO I lug media over to desktop and connect a cat5 cable to the router. Badaboom, I can see media from desktop, so all is OK there.

QUESTIONS
Here's what I need help with, and plain newbie English is great, but pointing me to useful links is good too.

I need to figure out what the problem is with the DVI setup. I have no clue how to proceed.

I also need some clues on how to get the router to see the wireless-N dongle. They are both from Buffalo so I was expecting this to be trivial. BUT the router has been flashed with DD-WRT-12319 so that may be an issue.

Next I need to find a way to set up file-sharing via the wireless-N link between the two boxes.


ANYBODY?  HEEELP!  :confused:

---

### Post by LowSky on 2009-09-03
plain english, ui assume the 8200 GPU is onboard, make sure the DVI is enabled from BIOS... many new boards need to be toggled, for instance mine has

VGA/HDMI
DVI/HDMI
VGA/DVI

---

### Post by jamesrfla on 2009-09-03
You can use Samba to setup file sharing. Here is a guide [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by chitowner2 on 2009-09-03
Thanks LowSky and james! 

I will check out those options, but for the DVI thing, that's a catch-22. Newbie that I am, I do not know how to monitor the boot process via, for example ssh or whatever, to be able to toggle options in BIOS.

I can see files, but don't know how to 'remote a gui desktop' for example.

---

### Post by bacardiandwatermelon on 2009-09-03
For kde I always had problems with wireless, you could use wicd instead, plus wireless doesn't start until you are logged in, so you will need to set your headless box to auto login. Sorry can't be much help with the dvi thing...

---

### Post by chitowner2 on 2009-09-03
OK I have looked into WICD and accept it as an option, but how do I get it installed if I have to do it remotely over something like ssh? 

Sorry friends but I am indeed clueless on this type of issue.  :-(

---

### Post by bacardiandwatermelon on 2009-09-04
I would drag it over to your router, and make sure the wireless network works before you setup ssh

---

### Post by chitowner2 on 2009-09-04
Update

I have resolved the DVI problem. I connected the DVI-out to a smaller Samsung monitor. I had to reboot but then some autodetect on the mobo gave me a display, so that issue is resolved.

I did sudo apt-get for WIDC and it did indeed replace the default Network Manager but came up saying "no wireless networks detected". Apparently this Buffalo USB dongle, a Belkin model and some others use the Ralink2870 chipset which I have now heard is an odd one and causes problems in *nix OS's. There *is* a driver for it  in Jaunty already but somehow WICD does not use it and there is dispute as to whether it fully supports 802.11 protocol.

SO
Now my issues have resolved into trying to find a way to get WICD to find the rt2870 driver and then recognize the USB device.

Any help on this one?

Thanks Folks!

---

