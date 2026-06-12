---
title: "analog sound?"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by adduds on 2011-02-19
only the left channel on my laptop is playing music....

the outputs are as follows everything looks ok? i think..? I'm still really new with linux only my second month

lspci -v

> 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0487
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at b4400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


aplay -l

> dad@parentop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by adduds on 2011-02-21
shameless bump

---

### Post by deckroid on 2011-02-22
I'll bump you. I have the same issue.  I have tried many things over the last 2 days. Read alot too.  Most were for older versions of Ubuntu.

---

### Post by Dutch70 on 2011-02-22
> **adduds said:**
> only the left channel on my laptop is playing music....

the outputs are as follows everything looks ok? i think..? I'm still really new with linux only my second month


Have you tried these troubleshooting steps?
[*[COLOR="Blue"]SoundTroubleShooting[/COLOR]*]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

### Post by mastablasta on 2011-02-22
Hello, 
What ubuntu verison are you guys using?
 
There is a bug in kernel that does this to intel sound module.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/536699)
 
solution is to update to latest alsa and then configure the card. troubl eis with every kernel update you will also get the same probelm repeated. doesn't help if you lock down the packages. the only "solution" would be to pin the kernel, but ofcourse your system won't get security updates then.
to upgrade alsa:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
Now the thing is that Alsa 1.0.23 is already in 10.10, however it seems as if it's missing some components. sudo alsaconfig (that will configure the card) does not seem to be a known command.
 
Anyway upond update and configure you can use HD sound, but it might dissapear (not load) every now and then. so the stable option to use is analog duplex.
 
Oh and for some people solution came when they changed AGP aperture size to 256MB in BIOS, but doesn't seem to help me.
 
good luck and i hope they solve this as these motherboard are more and more frequent.

---

### Post by deckroid on 2011-02-25
> **mastablasta said:**
> Hello, 
What ubuntu verison are you guys using?


I am using Ubuntu 10.10.

> 
 
... update to latest alsa and then configure the card. troubl eis with every kernel update you will also get the same probelm repeated. doesn't help if you lock down the packages. the only "solution" would be to pin the kernel, but ofcourse your system won't get security updates then.
to upgrade alsa:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
Now the thing is that Alsa 1.0.23 is already in 10.10, however it seems as if it's missing some components. sudo alsaconfig (that will configure the card) does not seem to be a known command.
 
Anyway upond update and configure you can use HD sound, but it might dissapear (not load) every now and then. so the stable option to use is analog duplex.
 
I tried this, but when I went to configure my sound, Alsa said it didn't find any sound cards present. Back at the desktop, there were no soundcards listed in Preferences>Sound.  I am really new to Linux and so I am sure I did something wrong, but I cannot figure out what I did. I reinstalled Ubuntu 10.10 (Not a horrible experience and quite quick!) and will try again tonight to see if I can get it right or mess up royally like I did the first time.

I will say, off topic kinda, that Ubuntu is a fun OS and I really like the command lines to do things.  Windows put up barriers between me and the computer.  I used to be a DOS guy, then Windows came along and I lost most of what I knew.  Even though DOS and Linux are not alike in many ways, the structure is basically the same.  

Ok, back on topic.  I will let you all know what occurs this time.  Maybe I will get lucky and it will work.  Analog duplex on my laptop sounds like an old transistor radio that is playing from inside my desk drawer.

Thanks for the info!

---

