---
title: "sound not working"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by gshockxc on 2009-07-20
All of a sudden, the sound is not working on my computer.  I'm running Kubuntu Jaunty.  I noticed it last night.  It booted up fine, and the sound played when I logged in.  I think I installed an update after that.  It was a little while later that I noticed my sound wasn't working when I played some YouTube videos.  Then I double-checked with some of my music files, and they would play in Amarok, but no sound.  However, I still have the system beep that tells me when I get a new email.  I have a Creative Soundblaster sound card, with a couple of standard computer speakers, and a small sub-woofer.  Not sure if that matters, but I thought I'd throw that out there.

Thanks in advance.

---

### Post by northern lights on 2009-07-20
Please post the outputs of```
sudo lshw -C display
```and```
aplay -l
```

---

### Post by gshockxc on 2009-07-20
> **northern lights said:**
> Please post the outputs of```
sudo lshw -C display
```and```
aplay -l
```
```
sudo lshw -C display
```

Results: 

```

  *-display
       description: VGA compatible controller
       product: GeForce 8800 GTS 512
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```


```
aplay -l
```

Results

```

card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm running Jaunty, not Ibex.  Sorry for that confusion.

Thanks for your help.

---

### Post by gshockxc on 2009-07-20
bump

---

### Post by gshockxc on 2009-07-20
I am stumped on this one.  Can anyone help here?  The sound played when I started up, and then it stopped working after I installed the updates.  I think the updates must have interfered with the audio driver, but I'm not sure how to reinstall them.  The sound card was automatically recognized when I installed Jaunty.

---

### Post by Java Geek on 2009-07-20
I had this same problem, and its was really simple really, right click the kMix in the System tray, Show Mixer Window, and then click Mixer and make sure everything is unmuted...

---

### Post by gshockxc on 2009-07-20
> **Java Geek said:**
> I had this same problem, and its was really simple really, right click the kMix in the System tray, Show Mixer Window, and then click Mixer and make sure everything is unmuted...

Yup, tried that.  That was one of my first thoughts.  No luck, but thanks, though.

The kMix window shows CA0106 at the top of the window.  I went into the System Settings and checked Multimedia.  There are 4 CA0106 devices, as well as a PulseAudio and 4 Audigy SE devices.  I can change the preferences for each one for any given audio output, but it has no effect.  

For now, I have CA0106 (IEC958 (S/PDIF) Digital Audio Output) set to the preferred device for all audio output.  But, like I said, it's not making any difference so far.  Still no sound.

... not that I know what any of those devices are, or what they represent.

---

### Post by Java Geek on 2009-07-20
Does this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303679]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303679") describe your problem?

---

### Post by gshockxc on 2009-07-20
> **Java Geek said:**
> Does this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303679]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303679") describe your problem?

It's very similar, yes.  Except, my distribution didn't change.  One minute it was working... and after I installed an update through the automated update notifier, it stopped.  I didn't notice it right away because I don't listen to music or watch videos that much.

I'll follow that link and see what I can find out.

Thanks.

---

### Post by gshockxc on 2009-07-20
OK, I followed the link and came up with similar results as the OP in that thread.  I ran the following commands
```

lspci -nn| grep audio

```

with the following result:
```

05:06.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]

```

and 

```

aplay -L

```

gave this:

```

front:CARD=CA0106,DEV=0
    CA0106, CA0106
    Front speakers
rear:CARD=CA0106,DEV=0
    CA0106, CA0106
    Rear speakers
center_lfe:CARD=CA0106,DEV=0
    CA0106, CA0106
    Center and Subwoofer speakers
side:CARD=CA0106,DEV=0
    CA0106, CA0106
    Side speakers
surround40:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CA0106,DEV=0
    CA0106, CA0106
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CA0106,DEV=0
    CA0106, CA0106
    IEC958 (S/PDIF) Digital Audio Output
null

```

I can only guess what's wrong here, but even if I'm close, I have no idea how to fix it.

---

### Post by Java Geek on 2009-07-20
> **gshockxc said:**
> OK, I followed the link and came up with similar results as the OP in that thread.  I ran the following commands
```

lspci -nn| grep audio

```

with the following result:
```

05:06.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]

```

and 

```

aplay -L

```

gave this:

```

front:CARD=CA0106,DEV=0
    CA0106, CA0106
    Front speakers
rear:CARD=CA0106,DEV=0
    CA0106, CA0106
    Rear speakers
center_lfe:CARD=CA0106,DEV=0
    CA0106, CA0106
    Center and Subwoofer speakers
side:CARD=CA0106,DEV=0
    CA0106, CA0106
    Side speakers
surround40:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CA0106,DEV=0
    CA0106, CA0106
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CA0106,DEV=0
    CA0106, CA0106
    IEC958 (S/PDIF) Digital Audio Output
null

```

I can only guess what's wrong here, but even if I'm close, I have no idea how to fix it.

Yah, sorry, thats as far as I know as well.

---

### Post by gshockxc on 2009-07-22
I'm still at a loss to figure out how to troubleshoot this.  

The sound was working, I installed some updates, and a while later I noticed that I had no sound.  I suspect that somehow the updates interfered with the Creative Sound Blaster card.  

Can anyone give me a hand with this?  Can I just reinstall the drivers?  How do I do that?  It was automatically recognized when I installed the first time.  I can't find any sound drivers in the repositories.

Thanks in advance.

---

