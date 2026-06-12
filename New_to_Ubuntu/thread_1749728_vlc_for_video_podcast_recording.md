---
title: "vlc for video podcast recording?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by tompoe on 2011-05-04
I just installed ubuntu 11.04 on desktop with logitech 9000 webcam.   I used software center to install vlc.  I want to try to set up to record video podcast for audio/video and when I clicked on capture device, it wanted me to enter path for audio and video.  The vlc text boxes are empty.

I tried typing: $ ls /dev/audio and ls /dev/video and got the following:
$ $ ls /dev/audio*
ls: cannot access /dev/audio*: No such file or directory
tom@taichi:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory

When I plug in webcam, I got the following:
$ $ ls /dev/video*
/dev/video0
tom@taichi:~$ ls /dev/audio*
ls: cannot access /dev/audio*: No such file or directory

Is there a way to identify what path to use for recording?  I have a microphone that I plug into the audio outlet on the sound card for Skype calls.  The webcam also has a microphone.

I'd like to just get a webcam app like guvcview, but that doesn't record sound and video.  Neither does Cheese.

---

### Post by shiman6 on 2011-08-13
> **tompoe said:**
> I just installed ubuntu 11.04 on desktop with logitech 9000 webcam.   I used software center to install vlc.  I want to try to set up to record video podcast for audio/video and when I clicked on capture device, it wanted me to enter path for audio and video.  The vlc text boxes are empty.

I tried typing: $ ls /dev/audio and ls /dev/video and got the following:
$ $ ls /dev/audio*
ls: cannot access /dev/audio*: No such file or directory
tom@taichi:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory

When I plug in webcam, I got the following:
$ $ ls /dev/video*
/dev/video0
tom@taichi:~$ ls /dev/audio*
ls: cannot access /dev/audio*: No such file or directory

Is there a way to identify what path to use for recording?  I have a microphone that I plug into the audio outlet on the sound card for Skype calls.  The webcam also has a microphone.

I'd like to just get a webcam app like guvcview, but that doesn't record sound and video.  Neither does Cheese.

For recording video, use /dev/video0 in the video device name section, under "Capture devices" and with V4l2. For recording audio, however, you need to identify the recording hardware you are going to use. 

Open the terminal, and put in "arecord -l". As an example, here's my output with my webcam plugged in: 

```

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: for [Microsoft® LifeCam HD-6000 for], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In this case, if you wish to use the webcam's audio, you would use hd:1 or hd:1,0 in the "Audio Device Name" section. For recording with a microphone through your sound card, you can either use hd:0 or hd:0,1. This may not work, sometimes, so you may have to put "pulse" in instead of hd:0. With this, you can just go to sound preferences and choose your input device. Or you can use Pulse Audio Volume Control (pavucontrol). 

With pavucontrol, once you get vlc started with "pulse" as "Audio Device Name", just go to the "Input Devices" tab in pavucontrol, and click the check mark next to the input you wish to use.

I hope this helps.

---

