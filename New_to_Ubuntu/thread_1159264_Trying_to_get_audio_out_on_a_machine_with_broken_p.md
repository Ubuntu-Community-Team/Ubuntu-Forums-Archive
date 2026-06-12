---
title: "Trying to get audio out on a machine with broken port"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by adaptives on 2009-05-14
Hello,

I have an Acer 6930 running Ubuntu 8.10 . A few days back a headphone plug broke in my headphone jack (S/PDIF). Since then I am trying to get audio out either on the 3rd audio port in my laptop or to my Bluetooth headset.

I have been reading various links and I have not been able to get stuff working. This process has been a good learning experience for many things, but I feel like if I get some basic answers I might be able to figure stuff out.

 I will appreciate any help for these questions:

1. My laptop has 3 audio jacks - S/PDIF, mic, the 3rd one has a ((o)) kind of symbol. Can I get audio out on this jack? I tried running
aplay -l 

The result is:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The analog device is my system speaker and the digital device seems to be the broken S/PDIF jack. The other jack does not appear in the output. So, is there any way I can configure the third port for audio out?

2. I tried getting my Bluetooth headset to work. I was able to scan the headset with 
hcitool scan

I also added some lines to ~.asoundrc and then I loaded the Bluetooth audio modules.

However when I tried to run:
pactl load-module module-alsa-sink device=bluetooth

I got a failure message: 'Failure: Module initalization failed'
If I try to run 
aplay -D bluetooth -f s16_le /path/to/mp3file

I get an error:
ALSA lib pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_bh_700.so
aplay: main:583: audio open error: No such file or directory

Is there some way to get either (third headphone jack or bluetooth audio out) of these working on my machine?
--
Thanks & Regards
Parag

---

### Post by lavinog on 2009-06-16
the ((o)) looks like the line out jack and should work with headphones. The problem I think is that with the headphone jack broken the mechanical switch might be disabling all outputs.

Is there no possible way to remove the headphone jack?
If you have a soldering iron you might be able to use a solder ball on a wire and attach it to the jack to pull it out.

---

