---
title: "Microphone menace"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by tweaktolive on 2011-04-01
Hi I am using Ubuntu 10.10 for about 5-6 months but the only thing that frustrates me is that i cannot activate my microphone .

When i insert the microphone jack and the headphone jack i have seen that only headphones work but microphones just do not want to respond.

I am searching the web but no solution..

I also have Windows XP(Dual Boot) and it works very well so its not a hardware problem....

Help anybody !!!!!!!!!:(

Thanx to anyone

---

### Post by Lateralis on 2011-04-01
Hi there. 

[This recent thread]("http://ubuntuforums.org/showthread.php?p=10616564#post10616564") might be of interest and might prove useful.  If it doesn't it would be helpful to know what hardware you have:

```

arecord -l
sudo lshw -C multimedia

```

The first (with a lowercase 'l' not a one) will tell us if your recording device is being picked up and if so how many sub-devices it has.  Sometimes Ubuntu chooses the "wrong" subdevice as your default device.  The second command will tell us all of the hardware specific information we should need.

---

### Post by tweaktolive on 2011-04-01
I didn't understand , but this is what i got:-


sharthak@Ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
sharthak@Ubuntu:~$ sudo lshw -C multimedia
[sudo] password for sharthak: 
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:44 memory:fea78000-fea7bfff
sharthak@Ubuntu:~$

---

### Post by Lateralis on 2011-04-01
OK, try the following, taken from the [Ubuntu Community sound troubleshoot]("https://help.ubuntu.com/community/SoundTroubleshooting").

> 
Getting Line Input to work (Microphone, etc)
Changing default subdevice configuration
Some sound devices have multiple capture subdevices (eg. hda-intel), but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. ALSA may not be configured to use your preferred device as subdevice #0 by default.
Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice.
Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case)
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized until it was repeated.
This also works if you use the "Options" tab in the standard mixer app to do the same thing.


---

