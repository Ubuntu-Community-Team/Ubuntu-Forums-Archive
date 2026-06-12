---
title: "Sound Card Drivers"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by JumpForJoy on 2010-01-22
Hi, I've recently installed Ubuntu on my new computer, that I built myself.  I used an old soundcard from an old computer I had laying around.  I then connected my digital Boston speakers.  I changed the output mode to digital under sound preferences, but there is a lag between when the computer sends sound to my speakers and when they make a sound.  I'm guessing this is do to me having *no* drivers installed, but I have no idea where to find them or what ones I need.  The delay is also very high, at like around 3-4 sec, even though this is fine for listening to music, it is very annoying for playing games.
I ran alsamixer and figured out that the card I'm using is:
> Card: SB Live! Value [CT4871]                                                &#9474;
&#9474; Chip: Cirrus Logic CS4297A rev 4                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]

All help would be greatly appreciated.
Thanks,
Jump For Joy

---

### Post by cariboo on 2010-01-23
Drivers in Linux are not like drivers in Windows. most drivrs are included with the kerenl, and are automagically loaded on boot. To check what driver is loaded for your audio device. Open an Applications->Accessories->Termianl and type the following command:

```
sudo lshw -C multimedia
```

this is what the output looks like on my system:

```
lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:dbf78000-dbf7bfff
```

note where it says driver=HDA, your driver will be different of course.

---

### Post by JumpForJoy on 2010-01-24
Hi, thanks for the help.  I ran "sudo lshw -C multimedia" and got this:
>   *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:e5200000-e5203fff

I did get "driver=HDA", does this mean that I don't have a driver problem, and I should be looking into something else?

Thanks for your help,
Jump For Joy

---

