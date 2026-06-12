---
title: "older TV Tuner is not working"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by illmatic on 2009-05-07
Hey there,

I'm trying to get my old TV tuner to work under linux 8.10.
I installed xawtv but I can hardly find any TV program. 

If I run dmesg | grep bttv I get following
```
alin@Alindesk:~$ dmesg | grep bttv  
[   14.090627] bttv: driver version 0.9.17 loaded
[   14.090631] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   14.097616] bttv: Bt8xx card found (0).
[   14.097637] bttv 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   14.097646] bttv0: Bt878 (rev 17) at 0000:01:06.0, irq: 18, latency: 32, mmio: 0xfdeff000
[   14.097660] bttv0: detected: FlyVideo 98FM (LR50)/ Typhoon TView TV/FM Tuner [card=36], PCI subsystem ID is 1852:1852
[   14.097663] bttv0: using: Lifeview FlyVideo 98FM LR50 / Typhoon TView TV/FM Tuner [card=36,autodetected]
[   14.097704] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   14.097765] bttv0: FlyVideo_gpio: unknown tuner type.
[   14.097767] bttv0: FlyVideo Radio=yes RemoteControl=yes Tuner=-1 gpio=0xffffff
[   14.097769] bttv0: FlyVideo  LR90=no  tda9821/tda9820=no  capture_only=no 
[   14.097771] bttv0: tuner type unset
[   14.097773] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   14.098342] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   14.098907] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   14.099559] bttv0: registered device video0
[   14.099592] bttv0: registered device vbi0
[   14.099624] bttv0: registered device radio0
[   14.099640] bttv0: PLL: 28636363 => 35468950 .. ok
[ 2927.338257] bttv0: PLL can sleep, using XTAL (28636363).
[ 2977.332031] bttv0: timeout: drop=345 irq=4915/165278, risc=7d56003c, bits: HSYNC OFLOW
[ 3004.454306] bttv0: reset, reinitialize
[ 3004.454338] bttv0: PLL can sleep, using XTAL (28636363).
[ 3602.645022] bttv0: timeout: drop=767 irq=9765/207650, risc=7d56003c, bits: HSYNC OFLOW
[ 3926.281041] bttv0: timeout: drop=4258 irq=44116/261367, risc=7d56003c, bits: HSYNC OFLOW
[ 4123.905828] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4128.589433] bttv0: PLL can sleep, using XTAL (28636363).
[ 4128.590486] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4133.318416] bttv0: PLL can sleep, using XTAL (28636363).
[ 4133.318817] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4140.856850] bttv0: PLL can sleep, using XTAL (28636363).
[ 4140.856895] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4144.326162] bttv0: PLL can sleep, using XTAL (28636363).
[ 4144.327048] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4147.310880] bttv0: PLL can sleep, using XTAL (28636363).
[ 4150.390979] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4153.776475] bttv0: PLL can sleep, using XTAL (28636363).
[ 4156.449906] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4159.992666] bttv0: PLL can sleep, using XTAL (28636363).
[ 4159.992714] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4163.530913] bttv0: PLL can sleep, using XTAL (28636363).
[ 4163.531847] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4168.886481] bttv0: PLL can sleep, using XTAL (28636363).
[ 4168.886529] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4175.402313] bttv0: reset, reinitialize
[ 4175.402363] bttv0: PLL: 28636363 => 35468950 . ok
[ 4248.389513] bttv0: PLL can sleep, using XTAL (28636363).
[ 4255.718951] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4416.368922] bttv0: PLL can sleep, using XTAL (28636363).
[ 4579.741962] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4615.222103] bttv0: PLL can sleep, using XTAL (28636363).
[ 4615.222134] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4641.422259] bttv0: PLL can sleep, using XTAL (28636363).
[ 4641.422294] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4673.396641] bttv0: PLL can sleep, using XTAL (28636363).
[ 4673.397227] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4700.436154] bttv0: PLL can sleep, using XTAL (28636363).
[ 4700.436187] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4727.589591] bttv0: PLL can sleep, using XTAL (28636363).
[ 4727.590172] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4754.569701] bttv0: PLL can sleep, using XTAL (28636363).
[ 4781.202791] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4812.210266] bttv0: PLL can sleep, using XTAL (28636363).
```

I think the TV tuner is recognized and the driver is installed too, so I'm wondering why nothing works.
I tried zapping some channels and I also tried scanning TV channels, but I could hardly find anything.

Does somebody have any Idea?
BTW Card Numer (36) is also correct.

I hope you know what I can do :)

Greets Illmatic

---

### Post by SteveDee on 2009-05-14
I have an old (analogue) TV card. I have not been able to run XawTV on Hardy, Intrepid or Jaunty. And if I run XawTV, the card won't work with other applications until I reboot Linux.

The app TVtime seems to work. Or you can test your card with VLC; Media > Open Capture Device:-
Capture mode: video for Linux 2
Device name: /dev/video0  {or your video "n"}
Input: 1 {to test with a direct video input, or 0 for tv}
Width: -1
Height: -1
Frequency: {if you selected "input=0" you need to enter the freq of a valid station}
...then hit Play.

I hope this is of some use...good luck!

---

### Post by illmatic on 2009-05-14
okay ty :)
I'll try it just if I'll get some spare time :)
(My to do list on my system is quite long though)
I'll report if it worked :)

---

### Post by johnaaronrose on 2009-05-15
Connected vhs tape player to Hauppage WinTV USB video grabber.

tvtime shows:
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/administrator/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: Device or resource busy

Tried your vlc suggestion. Doesn't show picture and no sound.

dmesg shows:
[  122.127605] usbvision_probe: Hauppauge WinTV USB Pro (PAL I,D/K) found
[  122.127659] USBVision[0]: registered USBVision Video device /dev/video0 [v4l2]
[  122.127684] USBVision[0]: registered USBVision VBI device /dev/vbi0 [v4l2] (Not Working Yet!)
[  122.516022] wlan0: no IPv6 routers present
[  123.084322] saa7115' 1-0025: saa7113 found (1f7113d0e100000) @ 0x4a (usbvision #0)
[  125.572038] Clocksource tsc unstable (delta = -277887859 ns)
[  125.592272] tuner' 1-0061: chip found @ 0xc2 (usbvision #0)
[  125.676311] tuner-simple 1-0061: creating new instance
[  125.676322] tuner-simple 1-0061: type set to 37 (LG PAL (newer TAPC series))
[  131.532049] tuner-simple 1-0061: destroying instance

Only just got this this usb device. I don't understand why PAL I,D/K. I thought that it would show PAL B (for Britain). Can you shed any light on this? Do you know of any usb video grabber (for laptop) that will work with jaunty?

---

### Post by SteveDee on 2009-05-15
> **johnaaronrose said:**
> Connected vhs tape player to Hauppage WinTV USB video grabber.

tvtime shows:
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/administrator/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: Device or resource busy

Tried your vlc suggestion. Doesn't show picture and no sound.


Only just got this this usb device. I don't understand why PAL I,D/K. I thought that it would show PAL B (for Britain). Can you shed any light on this? Do you know of any usb video grabber (for laptop) that will work with jaunty?

In Britain the standard is PAL-I (see link: [http://en.wikipedia.org/wiki/Pal#PAL_B.2C_G.2C_D.2C_K_or_I](http://en.wikipedia.org/wiki/Pal#PAL_B.2C_G.2C_D.2C_K_or_I)).

I've no experience with USB-TV but it looks like the Video For Linux driver (v4l2) does not support your stick. You could try looking here: [http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)  ...to see if your hardware is supported.

---

### Post by johnaaronrose on 2009-05-15
Thanks, SteveDee. I've looked before at that web site. When I click on a device (e.g. Hauppage PVRUSB2), I get 'The action you have requested is limited to users in the group user.'. Is there a way to see the device info when that happens?

However, at [http://www.linuxtv.org/wiki/index.php/USBVision_devices](http://www.linuxtv.org/wiki/index.php/USBVision_devices), my device (Hauppauge WinTV USB Pro (PAL I,D/K)                      [0573:4d29]) is listed. So it seems to be supported by the USBVision kernel module. lsmod shows usbvision module loaded. Any ideas?

---

### Post by oldos2er on 2009-05-15
I have an external Hauppauge WinTV-PVR USB2 device, which I use mainly in conjunction with "cat" or vlc to capture video from a VCR. There were a couple things I had to do to get it to work, 1), assuming you're using Gnome, check System, Administration, Users & Groups, check your username, under the tab User Privileges, make sure there is a check mark in front of "capture video from tv...." 2) Install the package ivtv-utils. If you intend to grab video from a VCR, run the command "ivtv-tune c3" if your VCR channel setting is set to 3 (or "ivtv-tune c4" if set to channel 4).

 Hope this helps.

---

### Post by johnaaronrose on 2009-05-16
Ann,

Thanks for your advice. I've already done: assuming you're using Gnome, check System, Administration, Users & Groups, check your username, under the tab User Privileges, make sure there is a check mark in front of "capture video from tv...." 2) Install the package ivtv-utils. If you intend to grab video from a VCR, run the command "ivtv-tune c3" if your VCR channel setting is set to 3 (or "ivtv-tune c4" if set to channel 4).

Re ivtv-tune, it won't allow me to set frequency table or channel for euroewest or uk-able (I'm in UK and want to use it for the Hauppage for copying from VHS tapes):
administrator@JohnLaptop:~$ ivtv-tune -l
Channels/Frequencies (MHz) for 'uk-cable':
administrator@JohnLaptop:~$ ivtv-tune -L
Frequency Maps:
us-bcast
us-cable
us-cable-hrc
us-cable-irc
japan-bcast
japan-cable
europe-west
europe-east
italy
newzealand
australia
ireland
france
china-bcast
southafrica
argentina
australia-optus
administrator@JohnLaptop:~$ ivtv-tune -teurope-west
ivtv-tune 1.50

Channel/Frequency changer for V4L2 compatible video encoders

Usage: ivtv-tune [OPTIONS]...

  -h, --help              Print help and exit
  -V, --version           Print version and exit
  -c, --channel=CHANNEL   set new channel
  -d, --device=DEVICE     set video device node
  -f, --frequency=FREQ    set new frequency (MHz)
  -l, --list-channels     list all channels and their frequencies  
                            (default=off)
  -L, --list-freqtable    list all available frequency mappings  (default=off)
  -t, --freqtable=STRING  set frequency map to use
  -x, --xawtv=CHANNEL     set new channel using custom map from ~/.xawtv
administrator@JohnLaptop:~$ ivtv-tune -l
Channels/Frequencies (MHz) for 'uk-cable':

v4l2-ctl allows me to set the input to composite video. I'll check that out further.

---

### Post by SteveDee on 2009-05-16
> **johnaaronrose said:**
> Thanks, SteveDee. I've looked before at that web site. When I click on a device (e.g. Hauppage PVRUSB2), I get 'The action you have requested is limited to users in the group user.'. Is there a way to see the device info when that happens?

However, at [http://www.linuxtv.org/wiki/index.php/USBVision_devices](http://www.linuxtv.org/wiki/index.php/USBVision_devices), my device (Hauppauge WinTV USB Pro (PAL I,D/K)                      [0573:4d29]) is listed. So it seems to be supported by the USBVision kernel module. lsmod shows usbvision module loaded. Any ideas?

Yes, some sections of that webs wiki need editing, but I found this link works for the PVRUSB2: [http://www.linuxtv.org/wiki/index.php/Pvrusb2](http://www.linuxtv.org/wiki/index.php/Pvrusb2)  ...and wonder if this indicates that your "Pro" device is supported. This external link from that page: [http://www.isely.net/pvrusb2/pvrusb2.html](http://www.isely.net/pvrusb2/pvrusb2.html) ...seems to indicate that the ivtv stuff is for pci cards, not USB, but I'm sure Ann has a much better idea than me as I don't have a USB device.

It would certainly be easier to follow the composite video route as you don't have to tune your USB device to see it working (and I assume your device has a yellow phono/RCA socket which supports composite video input).

---

