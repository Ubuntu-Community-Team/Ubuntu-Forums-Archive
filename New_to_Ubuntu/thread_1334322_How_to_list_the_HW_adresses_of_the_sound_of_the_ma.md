---
title: "How to list the HW adresses of the sound of the machine?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-11-22
it is for this : 
```
arecord -D hw:2,0 -r 32000 -c 2 -f S16_LE | aplay
```
but it says card not found

 cat /proc/asound/cards
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 22
** 1 [default        ]: USB-Audio - AK5370**
                      AKM              AK5370           at usb-0000:00:1d.0-1, full speed

```
I would like to record on this one: USB-Audio - AK5370



arecord -D /dev/dsp1 -d10800 -r44100 -c2 | lame -v --preset standard - tst.mp3
> ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp1
arecord: main:564: audio open error: No such file or directory
Warning: unsupported audio format



> 
$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [AK5370          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$  arecord -f cd -D hw:1,1 -d 20 test.wav
arecord: main:564: audio open error: No such file or directory




I did this : still same result

Setting default recording device

Editing ~/.asoundrc and putting this snippet below might work for some:

>  pcm.!default {
         type asym
         playback.pcm {
                 type plug
                 slave.pcm "hw:0,0"
         }
         capture.pcm {
                 type plug
                 slave.pcm "hw:1,0"
         } 
 }


--
wiki:[http://wiki.audacityteam.org/index.php?title=USB_mic_on_Linux](http://wiki.audacityteam.org/index.php?title=USB_mic_on_Linux)

---

### Post by spiderbatdad on 2009-11-22
the dev address is hw:1 try something like this:
```
 arecord -d 10 -f cd -t wav -D hw:1 foobar.wav
```

---

### Post by frenchn00b on 2009-11-22
:( :( :( 

```
#  arecord -d 10 -f cd -t wav -D hw:1 foobar.wav
Recording WAVE 'foobar.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
arecord: set_params:923: Channels count non available
```


# cat /etc/modprobe.d/sound.conf
```
## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-usb-audio

## module options should go here
options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1



```

---

### Post by spiderbatdad on 2009-11-22
ok but totally different error. try specifying your channel count again, the default is one, so include your -c2 from previous attempts.

---

### Post by frenchn00b on 2009-11-22
> **spiderbatdad said:**
> ok but totally different error. try specifying your channel count again, the default is one, so include your -c2 from previous attempts.



```

$  arecord -c2 -D hw:2,0  -d 10 -f cd -t wav foobar.wav
ALSA lib pcm_hw.c:1240:(_snd_pcm_hw_open) Invalid value for card
arecord: main:564: audio open error: No such file or directory
$  arecord -c2 -D hw:1,0  -d 10 -f cd -t wav foobar.wav
Recording WAVE 'foobar.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
arecord: set_params:923: Channels count non available
$  arecord -c2 -D hw:1,1  -d 10 -f cd -t wav foobar.wav
arecord: main:564: audio open error: No such file or directory
$  arecord -c2 -D hw:1,2  -d 10 -f cd -t wav foobar.wav
arecord: main:564: audio open error: No such file or directory

```

---

### Post by spiderbatdad on 2009-11-23
try substituting plughw for hw.

---

