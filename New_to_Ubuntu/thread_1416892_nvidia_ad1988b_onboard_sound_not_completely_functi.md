---
title: "nvidia ad1988b onboard sound not completely functional"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by filmdc on 2010-02-26
**nvidia ad1988b onboard Sound not completely functional**             
                                                                Hi,

My sound works alright by default, using the on-board soundcard. The problem I'm having is I cannot hear my inputs, through my output. My input 1, mic 1 and mic 2, all receive the input fine, and I can tell because volume meters show activity, but I can't hear anything through the mixer's output.

My motherboard is m2n-sli deluxe, with the nvidia nforce 570sli chipset. the audio is ad1988b.

I've followed a few different guides, including the comprehensive sound problem solutions.

My problem isn't that I can't hear audio if I play it directly from my OS, it's that I can't listen to inputs, despite clearly having good signal flow, etc. 


I have it set on Analog Stereo duplex, and I've tried all of the other variations with no joy. Can anyone help me out? I'm a newbie to the linux scene, but I'd like to work on getting my onboard sound completely functional, inputs and all.


**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
______________________________

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 81f6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

________________________________


I recently ran alsamixer, made sure my volumes were correct, and the started sound recorder. Sound recorder did record the input line! I can't hear it unless I play back a recording of it, but it is definitely there. i want to listen to the input. Thats where I'm at. How do i configure the sound card and software to send the input sound out of the output?

---

### Post by johngreth on 2010-02-27
The audio input is one of the few reasons I still dual boot windows. I'm curious though, because I never got any input, but you are. Maybe this can help: [http://ubuntuforums.org/showthread.php?t=406451](http://ubuntuforums.org/showthread.php?t=406451)

---

### Post by filmdc on 2010-02-28
Hey, I just got this to work!

On a fresh Ubuntu Karmic Koala I installed libao2 (searched alsa in the synaptic package manager) after installing the ALSA Mixer from the software center.

I loaded up the graphical interface Applications>>Sound and Video>>ALSA Mixer

and it showed me pretty much what you can see in the terminal version of the alsa mixer

except over the input sliders, there were two little buttons. i clicked them off, and  suddenly my input came in clear as day. 

did the terminal version of the alsa mixer have these option hidden, or is the graphical version just more prepared?

im not sure if the libao2 has anything to do with anything as of the moment. will get back to this.

---

