---
title: "no sound after installation"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by manasranjan on 2010-11-09
Hello,
I installed Ubuntu 10.10 in my computer, and after that, I have no sound at all. Here is the part of out put of my lspci -v | less, concerning the audio driver: ```
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```
Kindly tell me what I should do.

Manas

---

### Post by tea for one on 2010-11-09
Good morning

The first time I installed Ubuntu 10.10, the sound was muted. please double check the following:-

System > Preferences > Sound > Output Volume

Kind regards

---

### Post by sauravbhaumik on 2010-11-09
> **tea for one said:**
> Good morning

The first time I installed Ubuntu 10.10, the sound was muted. please double check the following:-

System > Preferences > Sound > Output Volume

Kind regards

I am writing on behalf of my friend, manasranjan. We ensured that the volume was set at the highest, and I also tried reinstalling some of the alsa packages in his computer, but to no avail. There is no sound at the bootup also.

---

### Post by mastablasta on 2010-11-09
have you already tried to upgrade alsa drivers?
 
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

### Post by manasranjan on 2010-11-09
> **mastablasta said:**
> have you already tried to upgrade alsa drivers?
 
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
It is already upgraded: ```
manas@manas-M68MT-D3:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.

```

---

### Post by mastablasta on 2010-11-09
did you also do this?:
 
```
 
sudo alsaconf

```

---

### Post by Crazedpsyc on 2010-11-09
try installing the Pulse Audio Device Chooser (padevchooser) from the synaptic and running it from Apps>Sound & Video>PulseAudio Device Chooser. It will open a notification are applet. Click on it and choose "Volume Control" In that new window try tweaking some settings (there are only a few to tweak) and see if it makes any difference. If there is still nothing look in the "Playback" tab and post what you see. If there is only System Sounds listed it may be something in the particular sound producing application that you are using.

---

### Post by manasranjan on 2010-11-09
After trying to manually install the new alsa driver (there was no alsa folder in /usr/src, so I thought I would need to install it manually), it gave some errors.  I was following the instructions given in [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) The output is given below:
```
manas@manas-M68MT-D3:/usr/src/alsa/alsa-driver-1.0.23$ sudo make
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/include'
make -C sound prepare
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/include/sound'
make prepare2
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/include/sound'
make[4]: Nothing to be done for `prepare2'.
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/include/sound'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/include/sound'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/include'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore/oss'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore/seq'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore/seq/oss'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore/seq/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore/seq'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/i2c'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/i2c/l3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/i2c/l3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/i2c/other'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/i2c/other'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/i2c'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl4'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl4'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1848'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1848'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/cs423x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/cs423x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/es1688'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/es1688'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/gus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/gus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/msnd'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/msnd'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/sb'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/sb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wavefront'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wavefront'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wss'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/synth'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/synth/emux'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/synth/emux'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/synth'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ac97'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ac97'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ali5451'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ali5451'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/asihpi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/asihpi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/au88x0'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/au88x0'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/aw2'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/aw2'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ca0106'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ca0106'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/hda'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/hda'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ice1712'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ice1712'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/korg1212'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/korg1212'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/mixart'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/mixart'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/nm256'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/nm256'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/oxygen'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/oxygen'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pdplus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pdplus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/riptide'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/riptide'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/rme9652'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/rme9652'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/trident'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/trident'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/vx222'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/vx222'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ymfpci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ymfpci'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/core'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/core'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/atmel'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/atmel'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/au1x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/au1x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/blackfin'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/blackfin'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/davinci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/davinci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/fsl'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/fsl'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/imx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/imx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/omap'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/omap'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/pxa'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/pxa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s6000'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s6000'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/sh'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/sh'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/txx9'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/txx9'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/caiaq'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/caiaq'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/misc'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/misc'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/usx2y'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/usx2y'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/misc'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/misc'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23'
make -C /lib/modules/2.6.35-22-generic-pae/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.23  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2232: note: this is the location of the previous definition
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2232: note: this is the location of the previous definition
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.o
In file included from /usr/src/alsa/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/alsa/alsa-driver-1.0.23/include/adriver.h:25,
                 from /usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:2:
/usr/src/alsa/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2232: note: this is the location of the previous definition
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
make: *** [compile] Error 2

```

But after that, as I thought since I didn't get through I should restart the machine, I rebooted it  and saw that the volume control applet turned inactive. There was no hardware found, while it had been showing my audio driver before. What should I do?

---

### Post by candtalan on 2010-11-09
Have you been able to run a live CD (your Ubuntu CD?) and does the live CD provide sound?

---

### Post by manasranjan on 2010-11-10
> **candtalan said:**
> Have you been able to run a live CD (your Ubuntu CD?) and does the live CD provide sound?
I don't have CD drive. I installed ubuntu from a usb pen drive.

---

### Post by candtalan on 2010-11-10
> **manasranjan said:**
> I don't have CD drive. I installed ubuntu from a usb pen drive.
OK!

The usb pen stick was probably a live usb - does it run and give sound, in a 'live' session? (that is, not from the installed session).

---

