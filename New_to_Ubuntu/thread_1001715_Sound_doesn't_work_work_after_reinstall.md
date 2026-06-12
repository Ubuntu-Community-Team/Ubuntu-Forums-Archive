---
title: "Sound doesn't work work after reinstall"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by triangleSLO on 2008-12-04
I had ubuntu running before and everything was OK, but yesterday i switched to fedora 10 for couple of hours :). I didn't like it so i reinstalled ubuntu II again and instead of drums i have some strange sound like some circuit is burning :)Which ever sound source i try the sound i get is the same. I dual boot and sound is ok in windows.  
I know ubuntu is punishing me for trying fedora, please help me out.
I have dell inspirion 6400 laptop and sigmatel audio device.

---

### Post by billgoldberg on 2008-12-04
> **triangleSLO said:**
> I had ubuntu running before and everything was OK, but yesterday i switched to fedora 10 for couple of hours :). I didn't like it so i reinstalled ubuntu II again and instead of drums i have some strange sound like some circuit is burning :)Which ever sound source i try the sound i get is the same. I dual boot and sound is ok in windows.  
I know ubuntu is punishing me for trying fedora, please help me out.
I have dell inspirion 6400 laptop and sigmatel audio device.

Make sure all your updates are installed.

I had this program in 8.10 RC but updates fixed it.

I'm not sure what you meant with sound sources, did you mean you tried Alsa or OSS instead of PulseAudio?

If not try that, it under system -> preferences -> sound.

Did that help?

---

### Post by triangleSLO on 2008-12-04
Thanks for fast reply. 
Yes i meant Alsa OSS and PulseAudio. All updates are installed, i tried all options in preferences -> sound but it doesnt help.

Damn Fedora curse :)

---

### Post by Michael.Godawski on 2008-12-04
Can you please post the output from:
```
aplay -l
```
```
find /lib/modules/`uname -r` | grep snd
```

---

### Post by triangleSLO on 2008-12-05
```
blaz@tancy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
blaz@tancy:~$ 

```

```
blaz@tancy:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.27-9-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/cs423x/snd-cs4231-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.27-9-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.27-9-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.27-9-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.27-9-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.27-9-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.27-9-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.27-9-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko

```

---

