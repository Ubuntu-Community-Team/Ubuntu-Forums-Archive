---
title: "Cannot load Nvidia driver on Ubuntu 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Dark Aspect on 2010-05-01
So, I have converted back to Ubuntu after a short and positive experience with Arch Linux and so far I am impressed with 10.04. However, it appears that I don't know what I am doing in terms of installing my video driver. I have a Nvidia Geforce 6800 and I get this message when trying to install the drivers off the main site:

> ERROR: Unable to load the kernel module ‘nvidia.ko’

I found [this]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") but it didn't help at all, I've blacklisted everything and still no go.

---

### Post by clhsharky on 2010-05-01
HI

Ubuntu Geek  is usually right on.

Try here

poor bootexperiance with proprietry nvidia driver (lucid)
[http://ubuntuforums.org/showthread.php?t=1468152](http://ubuntuforums.org/showthread.php?t=1468152)

Hope it help.

Sharky

---

### Post by Dark Aspect on 2010-05-01
> **clhsharky said:**
> Ubuntu Geek  is usually right on.


Well I think I am doing something wrong, I added the blacklist but it looks likes nouveau is still an active module:

```
fbcon 39270 71 - Live 0xffffffffa0276000
tileblit 2487 1 fbcon, Live 0xffffffffa0270000
font 8053 1 fbcon, Live 0xffffffffa0269000
bitblit 5811 1 fbcon, Live 0xffffffffa0262000
softcursor 1565 1 bitblit, Live 0xffffffffa0155000
nouveau 515131 2 - Live 0xffffffffa01cf000
[B]ttm 60815 1 nouveau, Live 0xffffffffa01b5000
drm_kms_helper 30742 1 nouveau, Live 0xffffffffa01a6000
drm 198770 4 nouveau,ttm,drm_kms_helper, Live 0xffffffffa0161000[/B]
i2c_algo_bit 6024 1 nouveau, Live 0xffffffffa014e000
binfmt_misc 7960 1 - Live 0xffffffffa00cb000
snd_mpu401 6875 0 - Live 0xffffffffa0081000
snd_mpu401_uart 6857 1 snd_mpu401, Live 0xffffffffa005a000
snd_seq_dummy 1782 0 - Live 0xffffffffa009f000
snd_intel8x0 31155 3 - Live 0xffffffffa0157000
snd_ac97_codec 125394 1 snd_intel8x0, Live 0xffffffffa012d000
ac97_bus 1450 1 snd_ac97_codec, Live 0xffffffffa0079000
snd_pcm_oss 41394 0 - Live 0xffffffffa0120000
snd_seq_oss 31219 0 - Live 0xffffffffa0116000
snd_mixer_oss 16299 1 snd_pcm_oss, Live 0xffffffffa004f000
snd_seq_midi 5829 0 - Live 0xffffffffa0062000
snd_pcm 87850 4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xffffffffa00fe000
snd_rawmidi 23388 2 snd_mpu401_uart,snd_seq_midi, Live 0xffffffffa00f6000
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi, Live 0xffffffffa003f000
snd_seq 57417 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa00e5000
snd_timer 23553 2 snd_pcm,snd_seq, Live 0xffffffffa0092000
snd_seq_device 6824 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa0035000
ppdev 6375 0 - Live 0xffffffffa0021000
ns558 3704 0 - Live 0xffffffffa0017000
gameport 10966 2 ns558, Live 0xffffffffa0012000
snd 70978 17 snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa00d1000
psmouse 64608 0 - Live 0xffffffffa00b9000
serio_raw 4918 0 - Live 0xffffffffa00b2000
parport_pc 29958 1 - Live 0xffffffffa00a2000
asus_atk0110 10033 0 - Live 0xffffffffa009a000
edac_core 45423 0 - Live 0xffffffffa0084000
edac_mce_amd 9214 0 - Live 0xffffffffa007c000
k8temp 3912 0 - Live 0xffffffffa0076000
soundcore 8052 1 snd, Live 0xffffffffa006e000
snd_page_alloc 8500 2 snd_intel8x0,snd_pcm, Live 0xffffffffa0065000
i2c_nforce2 6099 0 - Live 0xffffffffa005e000
lp 9336 0 - Live 0xffffffffa0055000
parport 37160 3 ppdev,parport_pc,lp, Live 0xffffffffa0043000
pata_amd 11962 0 - Live 0xffffffffa003a000
forcedeth 55592 0 - Live 0xffffffffa0025000
sata_nv 23778 2 - Live 0xffffffffa0019000
floppy 63156 0 - Live 0xffffffffa0000000

```

Solution:
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo modprobe -r nouveau
sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run

---

### Post by myromance123 on 2010-05-02
> Solution:
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo modprobe -r nouveau

Thanks so much Dark Aspect :)
I am now able to install the drivers like how I normally do.

I tried what Ubuntu Geek instructed to do, but it doesn't work for me.

:KS

---

### Post by gab1x on 2010-05-04
I posting this to help others ...

I had exactly the same problem with ¨Cannot load nvidia.ko ... ¨ and ¨modprobe -r nouveau¨ -> nouveau **IN USE**

I did the following:

1. fresh install - because i had 32bit
> Ubuntu 10.04 x86_64
2. downloaded nvidia driver from nvidia.com
> NVIDIA-Linux-x86_64-195.36.24-pkg2
3. Did the blacklisting - [Howto install nVIDIA drivers manually on Ubuntu 10.04 (Lucid Lynx)]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
> gsudo gedit /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv


4. then to be sure -> 
> sudo apt-get --purge remove nvidia-*

!! 5. Reboot !!! - THE RECOVERY MODE IS THE MOST IMPORTANT PART OF THE WHOLE PROCESS
> GRUB -> Choose (recovery mode)

6. In the selection menu -> *_drop to root shell_* then
> init 3

7. installed the driver with
> sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2 

8. It worked ,without any problem ...


Hope it helps ...

:)

**P.S. :** I am not sure if step 3. and 4. is required. Now it`s your job to test it.
**P.S. 2 :** I think , I also installed _linux-headers-2.6.32-21-generic_ via apt-get [

**EDIT 14.5.2010 :** 

In case of : **"Error: unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernal source files for your kernel and that they are properly configured..."**


> sudo apt-get install linux-headers-`uname -r`

---

### Post by jstateson on 2010-05-08
Thanks - had the exact same problem and purging nouveau fixed it!

---

### Post by myromance123 on 2010-05-11
gab1x,

 I was wondering, what kernel version are you using?
I'm trying Ubuntu Studio 10.04, and this is my first 64 bit OS I've ever used.
Even though I followed your methods described, I continuously get this:
"Error: unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernal source files for your kernel and that they are properly configured..."

On another forum, a 64bit user mentioned that 195.36.15 would work but it doesn't as well.

How would I go about getting Nvidia's drivers to work with kernel 2.6.33 ?
Purging nouveau and/or nvidia-* so far hasn't helped. Neither has blacklisting.


EDIT: Alright, the only step I was missing besides all the steps gab1x listed was installing the kernel headers.
After following a link gab1x pm'ed me, this is the last step:
```
sudo apt-get install linux-headers-`uname -r` 
```
After that I was able to install the driver. Thanks gab1x :)

---

### Post by The Bright Side on 2010-05-15
Hey guys,

I just installed the new NVidia drivers according to the instructions above (great btw! this should be sticky), but now, when I look into my Preferences or Administation menus, I can't find the NVidia system settings anywhere. They used to be there when I installed those drivers in 9.10...

Any ideas?

M.

---

### Post by gab1x on 2010-05-15
> **The Bright Side said:**
> Hey guys,

I just installed the new NVidia drivers according to the instructions above (great btw! this should be sticky), but now, when I look into my Preferences or Administation menus, I can't find the NVidia system settings anywhere. They used to be there when I installed those drivers in 9.10...

Any ideas?

M.

[LIST]
[*]open console
[*]sudo nvidia-settings
[/LIST]

Btw : I hadn't such problem.

---

### Post by The Bright Side on 2010-05-15
Thanks! Got it! :-)

---

### Post by balthorium on 2010-07-19
Gab1x - thanks a bunch for posting those instructions!  I'm running Ubuntu 10.04 on a Lenovo W510 and your procedure worked perfectly.  For the record, step 3 was required for me, however step 4 was not (though there were some existing nvidia-* packages already installed, it didn't seem to matter). 

Cheers

---

### Post by oldsoundguy on 2010-07-19
I have an issue with the NVidia driver also.  But a bit different.

First, to get ANY working display to support my monitor (a high end wide screen HP cinema monitor), I had to remove the xorg file completely  (sudo rm xorg.conf) .. and then re-boot. It loaded the UBUNTU drivers.
Most of the monitor functionalities were there then including the high resolution and the ability to rotate the monitor to portrait orientation.

BUT, the NVida-current drivers are installed, but I get the message of "not activated" in the drivers window.  
Can NOT figure out what is going on with that.
Would be nice to have more video bells and whistles ... but this is not earth shattering and something to snivel about .. as it DOES work as  is!

---

### Post by leclerc65 on 2010-07-19
* deleted

---

### Post by nickopen on 2010-08-07
I'm having issues unloading nouveau with the new kernel (2.6.32-24-generic). All the above instructions worked fine for me on the previous versions.

Now, no matter what I do, I can't seem to stop nouveau from loading. I have it blacklisted, I use the recovery console, I added rdblacklist=nouveau to the grub command line and it STILL loads nouveau.

Help! please!

Edit - found the solution:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)
You need to add "nomodeset" to the boot cmd.

---

### Post by oc2010 on 2011-05-15
It works like a charm for Ubuntu 10.04 and Nvidia Geforce 9800 GX2 :P

---

