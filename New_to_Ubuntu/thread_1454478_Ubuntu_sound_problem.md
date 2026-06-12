---
title: "Ubuntu sound problem"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by cuberts on 2010-04-14
Hi, I am new to Ubuntu and I am enjoying it very much. But I am having a problem with sound. My speakers are not working at all. When I open up Windows XP, they work perfectly fine, but now they dont make  a sound. I was wondering if somebody could help me with this. Also I am using Ubuntu 9.10

---

### Post by ttshivers on 2010-04-14
I've tried to help him by installing the drivers for it and stuff like that, but it still doesn't work.

---

### Post by partloer on 2010-04-14
Hi cuberts,

Here are a few ideas to start with
[LIST=1]
[*]System -> Administration -> Hardware Drivers see if there are any audio drivers to install
[*]System -> Preferences -> Sound see if your hardware shows up and that the output is selected to the correct device
[*]Try this link [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+troubleshooting]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+troubleshooting")
[*]Try looking on the forums and google for your hardware and any problems
[*]Give more information about your hardware and I will see if I can help anymore
[/LIST]

---

### Post by Old and Rusty on 2010-04-14
Two computers I look after suddenly did the same thing.  Sound stopped.  I sniffed around and found that the sound was configured to digital out on both systems.  My theory is that the software was updated and was preset to digital.  I selected analog sound and both computers are just fine.  My own did not suffer this problem and I don't know why.

---

### Post by lidex on 2010-04-14
> **cuberts said:**
> Hi, I am new to Ubuntu and I am enjoying it very much. But I am having a problem with sound. My speakers are not working at all. When I open up Windows XP, they work perfectly fine, but now they dont make  a sound. I was wondering if somebody could help me with this. Also I am using Ubuntu 9.10

Have a look at this page to troubleshoot the generic sound issues in karmic:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Any questions - post here.

---

### Post by lonewolfandcub on 2010-04-14
> **cuberts said:**
> Hi, I am new to Ubuntu and I am enjoying it very much. But I am having a problem with sound. My speakers are not working at all. When I open up Windows XP, they work perfectly fine, but now they dont make a sound. I was wondering if somebody could help me with this. Also I am using Ubuntu 9.10
 
 
So did I, the problem was the on board sound and the SoundBlaster card. I had de-activated the onboard sound card and was channelling sound through the Sound Blaster, but the OS didn't know that. So after a bit of fiddling in the control panel, I managed to resart the sound and now it works fine.:guitar:

---

### Post by oleink on 2010-04-14
It may be your actual settings and not the sound drivers

---

### Post by ttshivers on 2010-04-14
Oh.  I forgot to include some results of commands that it said to type on a webpage to see what sound card he had.

[B]Result from running the command alsamixer

[/B]Card: Intel ICH5
Chip: analog devices AD 1980
View: playback
Item: Master [dB gain=0.00, 0.00]

[B]Result from running the command aplay -1

[/B]****List of PLAYBACK Hardware Devices****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by oleink on 2010-04-15
Is there a way to change it to output/input?

---

### Post by partloer on 2010-04-15
> **oleink said:**
> Is there a way to change it to output/input?

A few options
[LIST=1]
[*]alasmixer command then F4
[*]System -> Sounds -> Hardware tab should list the devices Input and Output tabs allow control of device
[/LIST]

---

### Post by ttshivers on 2010-04-15
Cuberts,

Also run these codes so we can see more information about your hardware.
     Code:

 lspci > ~/Desktop/lspci.txt
aplay -l >> ~/Desktop/soundinfo.txt
alsactl -v >> ~/Desktop/soundinfo.txt
uname -a >> ~/Desktop/soundinfo.txt 

The terminal is accessable through Applications -> Accessories -> Terminal.

Then, just attach soundinfo.txt and lspci.txt (their on your desktop) to your post.

---

### Post by ttshivers on 2010-04-15
Have you updated Ubuntu recently?  They might have a patch for your sound card driver.

---

### Post by lidex on 2010-04-15
Go back to that page in post #5 and install the alsa-backports.
Next run these in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Now REBOOT. Check levels in alsamixer Still no sound? Run this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
and post results here.

---

### Post by oleink on 2010-04-15
Thats what youll need

---

### Post by mhgsys on 2010-04-28
Since you seem to have 2 threads about this; also posting it here. 

> **mhgsys said:**
> There was a bug in 9.10 which also had a problem with my [SiS] Azalia Audio Controller

It was send to sleepmode and could not wake up.
Fixed it with;

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

change the line
```
options snd-hda-intel power_save=10 power_save_controller=N
```

into

```
options snd-hda-intel power_save=0 power_save_controller=N
```

---

### Post by ttshivers on 2010-05-03
Hey Cuberts.  Mark this thread as solved because I solved your sound problem.

---

