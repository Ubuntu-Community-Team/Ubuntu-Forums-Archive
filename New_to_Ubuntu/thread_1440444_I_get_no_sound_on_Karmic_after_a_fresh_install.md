---
title: "I get no sound on Karmic after a fresh install"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by malaikaangel on 2010-03-27
Hello
I have a Sony Vaio (VPCEB1M1E) and I just installed Karmic Koala from a CD next to Windows 7. Everything works... except I can't get any sound at all. I've tried doing what others did on different links and threads but I am an absolute beginner and really not sure what I'm doing.
Here's what I get for aplay -l

Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC269 Analog [ALC269 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  1: Generic [HD-Audio Generic], périphérique 3 : ATI HDMI [ATI HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

Help... please...

---

### Post by Didius Falco on 2010-03-27
Since the aplay -l shows that it is seeing your sound  sources, it may be as simple as the volume being turned all the way down.

Here is a great guide to fixing the sound: [http://ubuntuforums.org/showthread.php?t=205449&highlight=pulse+audio](http://ubuntuforums.org/showthread.php?t=205449&highlight=pulse+audio)

I recommend jumping directly to the alsamixer section. If it is the volume turned all the way down, or the source muted, this will be a quick fix for it. If that doesn't do the trick, just keep following the guide.

I hope this helps!!

Regards,

Didius

---

### Post by NightwishFan on 2010-03-27
Check the volume with this command:
```
alsamixer -c0
```

---

### Post by malaikaangel on 2010-03-28
Thanks.
I checked alsamixer and everything is turned to max. I also followed the guide but nothing. The only thing now is that when I reboot, the sound does not go back to mute like before.

---

### Post by malaikaangel on 2010-03-30
Bump!

---

### Post by reivilo78 on 2010-04-11
Hello,

I have exactly the same laptop and same version of Ubuntu as you.
Here is how i got it working :

Go here :

[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

run the first two commands in a terminal.

Look for Node[0x19] PIN then change in the "Widget Control" group box the value "VREF" from whatever it is to HIZ or GRD.
Close the application and select No when it asks you if you want to revert the changes you just made.

Aparently you have to do this everytime you reboot though....

---

### Post by lidex on 2010-04-11
Go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
and work through the guide first. Report your results.

edit: Make sure to install alsa-backports.

---

### Post by lidex on 2010-04-11
Still no sound? Try this. In a terminal="Applications>Accessories>Terminal"
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
to edit the file. Add this line at the bottom:
```
options snd-hda-intel enable=1 model=sony-assamd
```
Save. Close. Reboot. Check alsamixer settings:
```
alsamixer
```

---

### Post by stevek123 on 2010-04-11
I have to reconfig my sound module every time I upgrade kernel.
Directions are here =Comprehensive sound Problems Guide
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by reivilo78 on 2010-04-11
> **lidex said:**
> 
```
options snd-hda-intel enable=1 model=sony-assamd
``` 

Hey, this laptop uses the ALC269 Codec which does not list sony-assamd as available model.
Available models are :

```

ALC269
======
  basic        Basic preset
  quanta    Quanta FL1
  eeepc-p703    ASUS Eeepc P703 P900A
  eeepc-p901    ASUS Eeepc P901 S101
  fujitsu    FSC Amilo
  auto        auto-config reading BIOS (default)

```This laptop is pretty recent so I don't think this is a matter of backports/kernel upgrading.

Here is the bugtrack for this problem (seems to be common for all sony VPC-EB**** laptops) :
[0004934: No sound on a Sony Vaio VPC EB1J1E (hda-intel - Realtek ALC269 and Intel G45 DEVIBX codecs) - ALSA bugtracking system]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934")

---

### Post by lidex on 2010-04-11
> **reivilo78 said:**
> Hey, this laptop uses the ALC269 Codec which does not list sony-assamd as available model.
Those are just models that were reported as working. There are a number of options that don't make sense that are working for people out there.
[http://ubuntuforums.org/showthread.php?t=1043568]("http://ubuntuforums.org/showthread.php?t=1043568")

> This laptop is pretty recent so I don't think this is a matter of backports/kernel upgrading.

Your logic is faulty. In fact, the opposite is true. Ubuntu drivers lag behind the newer hardware which is why the backports exist in the first place.

---

### Post by reivilo78 on 2010-04-11
I managed to make the change persistent by running a command line program (hda-verb) that does the exact same thing as the HDA Analyzer.
This can be used until the Alsa team fixes the Alsa Driver for Sony VPCEB1**** laptops.


```

sudo -s
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz
tar xvzf hda-verb-0.3.tar.gz
cd hda-verb-0.3
make
cp hda-verb /usr/bin

```then go to System menu, Preference, Startup Applications, Add and in Name put anything you want(i put "sound fix"), in Command put this :

```

hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x22

```

---

