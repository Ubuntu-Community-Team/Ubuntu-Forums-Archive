---
title: "where to place? The driver from ralink's website to get my wireless connection going."
date: 2011-06-18
forum: New to Ubuntu
---

### Post by TMundo on 2011-06-18
Just downloaded the driver form my Wireless Linksys E1000 router.

The file is called:

2010_0709_RT2870_Linux_STA_v2.4.0.1.tar.bz2

I have no idea where to put it, it's on my desktop in Windows right now, which I'm running alongside Ubuntu until I get everything working properly.

Is there a folder/directory I can drop it into from the windows side?  The directions from the site I found the link to ralink's site where I got the file are very confusing, and they are talking about another file altogether for their example.

[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

Here's a link to the page where I found the file on Ralink's site

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

you can see the file: RT2870USB(RT2870/RT2770) listed there.

Where do I put it?  It seems to be the correct file, so I don't think I need to edit it, nor would I know how to do so.

Here's my lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

Any help would be much appreciated, I really am excited to get Linux up and running.

thanx

---

### Post by wildmanne39 on 2011-06-18
> **TMundo said:**
> Just downloaded the driver form my Wireless Linksys E1000 router.

The file is called:

2010_0709_RT2870_Linux_STA_v2.4.0.1.tar.bz2

I have no idea where to put it, it's on my desktop in Windows right now, which I'm running alongside Ubuntu until I get everything working properly.

Is there a folder/directory I can drop it into from the windows side?  The directions from the site I found the link to ralink's site where I got the file are very confusing, and they are talking about another file altogether for their example.

[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

Here's a link to the page where I found the file on Ralink's site

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

you can see the file: RT2870USB(RT2870/RT2770) listed there.

Where do I put it?  It seems to be the correct file, so I don't think I need to edit it, nor would I know how to do so.

Here's my lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

Any help would be much appreciated, I really am excited to get Linux up and running.

thanxHi, you need to install it from ubuntu, you can not do it from windows, I do not think the way you are doing it is needed, but if you have to have that driver put it in you documents folder in windows then boot ubuntu and you can click on the file from ubuntu and move it to ubuntu.

---

### Post by TMundo on 2011-06-18
Yes, I know I can do it that way, but i don't know where or how to install it from Ubuntu.  I don't think I can simply click on it in Ubuntu, I have to put it somewhere.

---

### Post by Talon2 on 2011-06-19
> **TMundo said:**
> Yes, I know I can do it that way, but i don't know where or how to install it from Ubuntu.

I'd suggest the first step is to determine if you need this file.

What version of Ubuntu are you running?

If the answer is 11.04, you do not need the file and the device should be working.  What caused you to think you need this file?

If the answer is a version earlier than 11.04, this device will be a pain.  I recommend you use version 11.04.

---

### Post by dFlyer on 2011-06-19
Without going to the links you provided, when you extract this file do you have to compile it (ie configure, make, make install). If this is the case it can be really hard. The question above ask what version of ubuntu you are running? If it's not 11.04 maybe it's time to think about moving up to 11.04 if the driver is already provided in the archives or kernel, as stated by the above link.

---

### Post by wildmanne39 on 2011-06-19
> **TMundo said:**
> Yes, I know I can do it that way, but i don't know where or how to install it from Ubuntu.  I don't think I can simply click on it in Ubuntu, I have to put it somewhere.I agree have your computer connected to the internet by a hard wire, then start you computer and hopefully you will see a window pop up that will install the driver for you, I have wireless that I do not use but is is connected, I checked and it is the same one you have. When I installed I chose to install with ubuntu downloading all updates and third party software and when I restarted it found and activate my wireless, it did not even show a screen. I have not  used it but a couple of times and it was about a month before I checked to see if it was working. If it does not give you the option to enable your wireless from the icon on the top right of the screen open software center or synaptic and install the driver from there.

---

### Post by 3rdalbum on 2011-06-19
The device should work out-of-the-box on Ubuntu 11.04. If you are using an earlier version of Ubuntu you might need to blacklist (prevent from loading) a particular other driver that erroneously attaches itself to your wifi device. There are instructions for this floating around on the internet - just look up "RT2870 ubuntu *your ubuntu version*" on Google for instructions.

---

### Post by wildmanne39 on 2011-06-27
Hi, I am giving you a link to help you get it working, you will have to follow the instructions carefully and see if it fixes your problem, I just got out of the hospital so I am not helping anyone right now I am just to sick, I just got on for a minute to look something up and I saw your message. I hope this helps, you may have to  do a google search if you need more help.                               
  [http://ubuntuforums.org/showthread.php?t=1665389&highlight=RT2870%2FRT3070+Wireless+Adapter](http://ubuntuforums.org/showthread.php?t=1665389&highlight=RT2870%2FRT3070+Wireless+Adapter)

---

### Post by josephmills on 2011-06-27
just for next time if you would like to compile your own driver you have to down load the ubuntu or deb tar file then open you terminal and go to root (sudo -s) then cd to the downloads folder and then un tar it ( tar -zxvf yourfile.tar )  then cd into that file then read theh read me file. it will tell you what to do. install kernel header (apt-cache search linux-headers-$(uname -r)) then make then a make install and it will compile it for you and put it in the dir itself looks like you driver should work out of the box but if you like to compile there you go.

---

### Post by josephmills on 2011-06-27
ok I got your pm here we go lets see if we can take care of it with checking your mods to make sure that to many are not loaded open your terminal and type in ```
lsmod 
``` paste that here.  that will give us a idea of what to blacklist.

---

### Post by TMundo on 2011-06-27
Okay, after lsmod was put in the terminal, here is the output:

Module                  Size  Used by 
snd_hda_codec_idt      60537  1 
snd_usb_audio          91410  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel 
nouveau               621970  2 
binfmt_misc            13213  1 
snd_pcm                80244  3 snd_usb_audio,snd_hda_intel,snd_hda_codec 
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec 
snd_usbmidi_lib        24388  1 snd_usb_audio 
ttm                    65184  1 nouveau 
snd_seq_midi           13132  0 
drm_kms_helper         40745  1 nouveau 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
drm                   180037  4 nouveau,ttm,drm_kms_helper 
ppdev                  12849  0 
gspca_zc3xx            50969  0 
snd_timer              28659  2 snd_pcm,snd_seq 
dcdbas                 14054  0 
gspca_main             27894  1 gspca_zc3xx 
snd_seq_device         14110  3 snd_seq_midi,snd_seq,snd_rawmidi 
videodev               75143  1 gspca_main 
psmouse                73312  0 
i82975x_edac           12858  0 
parport_pc             32111  1 
serio_raw              12990  0 
i2c_algo_bit           13184  1 nouveau 
video                  18951  1 nouveau 
snd                    55295  17 snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device 
edac_core              42881  1 i82975x_edac 
soundcore              12600  1 snd 
rt2870sta             410104  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
crc_ccitt              12595  1 rt2870sta 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp 
usbhid                 41704  0 
hid                    77084  1 usbhid 
tg3                   131476  0 
ahci                   21591  3 
libahci                25548  1 ahci 

also, I don't know if it will help, but on another thread, someone had asked to put in the command: 

lsusb
modinfo rt2870sta
lsmod | grep rt2

for which the output was:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
tmundo@tmundo-Precision-WorkStation-390:~$ modinfo rt2870sta 
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/rt2870sta.ko 
version:        2.1.0.0 
license:        GPL 
description:    RT2870/RT3070 Wireless Lan Linux Driver 
author:         Paul Lin <paul_lin@ralinktech.com> 
firmware:       rt3071.bin 
firmware:       rt3070.bin 
firmware:       rt2870.bin 
srcversion:     93C0C58E1A016FE5BD4DC9F 
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip* 
depends:        crc-ccitt 
staging:        Y 
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp) 
tmundo@tmundo-Precision-WorkStation-390:~$ lsmod | grep rt2 

and there you are, what next?

---

### Post by josephmills on 2011-06-27
> **TMundo said:**
> Okay, after lsmod was put in the terminal, here is the output:

Module                  Size  Used by 
snd_hda_codec_idt      60537  1 
snd_usb_audio          91410  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel 
nouveau               621970  2 
binfmt_misc            13213  1 
snd_pcm                80244  3 snd_usb_audio,snd_hda_intel,snd_hda_codec 
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec 
snd_usbmidi_lib        24388  1 snd_usb_audio 
ttm                    65184  1 nouveau 
snd_seq_midi           13132  0 
drm_kms_helper         40745  1 nouveau 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
drm                   180037  4 nouveau,ttm,drm_kms_helper 
ppdev                  12849  0 
gspca_zc3xx            50969  0 
snd_timer              28659  2 snd_pcm,snd_seq 
dcdbas                 14054  0 
gspca_main             27894  1 gspca_zc3xx 
snd_seq_device         14110  3 snd_seq_midi,snd_seq,snd_rawmidi 
videodev               75143  1 gspca_main 
psmouse                73312  0 
i82975x_edac           12858  0 
parport_pc             32111  1 
serio_raw              12990  0 
i2c_algo_bit           13184  1 nouveau 
video                  18951  1 nouveau 
snd                    55295  17 snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device 
edac_core              42881  1 i82975x_edac 
soundcore              12600  1 snd 
[COLOR="Red"]rt2870sta             410104  0 [/COLOR]
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
[COLOR="red"]crc_ccitt              12595  1 rt2870sta [/color]
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp 
usbhid                 41704  0 
hid                    77084  1 usbhid 
tg3                   131476  0 
ahci                   21591  3 
libahci                25548  1 ahci 

also, I don't know if it will help, but on another thread, someone had asked to put in the command: 

lsusb
modinfo rt2870sta
lsmod | grep rt2

for which the output was:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
tmundo@tmundo-Precision-WorkStation-390:~$ modinfo rt2870sta 
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/rt2870sta.ko 
version:        2.1.0.0 
license:        GPL 
description:    RT2870/RT3070 Wireless Lan Linux Driver 
author:         Paul Lin <paul_lin@ralinktech.com> 
[COLOR="Red"]firmware:       rt3071.bin 
firmware:       rt3070.bin 
firmware:       rt2870.bin [/COLOR]
srcversion:     93C0C58E1A016FE5BD4DC9F 
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip* 
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip* 
[COLOR="Red"]depends:        crc-ccitt [/COLOR]
staging:        Y 
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp) 
tmundo@tmundo-Precision-WorkStation-390:~$ lsmod | grep rt2 

and there you are, what next?
sorry I got caught up in a intense game of monopoly  but...
try ```
sudo modprob rt2870sta 
```  anything? Before we put on are linux trifocals can we also see a ```
rfkill list all 
``` and a ```
ls /lib/firmware/ | grep rt

```thanks

---

### Post by TMundo on 2011-06-28
Okay,

     Here are the codes you told me to input, and the outputs that occured as a result:

Code:

sudo modprob rt2870sta

Output:

sudo: modprob: command not found 


Code:

rfkill list all

Output:

*Nothing*


Code:

ls /lib/firmware/ | grep rt

Output:

edgeport 
intelliport2.bin 
libertas 
rt2561.bin 
rt2561s.bin 
rt2661.bin 
rt2860.bin 
rt2870.bin 
rt3070.bin 
rt3071.bin 
rt3090.bin 
rt73.bin 
rtl_nic 
rtlwifi 

the first one initially prompted me to enter my password before it said command not found.  The second one literally did nothing but bring up the usuall prompt again, and the third spit out a bit of info.

---

### Post by josephmills on 2011-06-28
typo ```
sudo modprobe rt2870sta 
``` sorry again

---

### Post by TMundo on 2011-06-28
no output, just the prompt again.

---

### Post by josephmills on 2011-06-28
> **TMundo said:**
> no output, just the prompt again.
unplug the wireless usb and then do the modprobe again put it back in the usb slot. then let us see a  ```
iwlist scan 
```

**NOTE you should take out the address I just want to see if it is seeing networks. **

---

