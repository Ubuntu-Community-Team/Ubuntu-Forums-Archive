---
title: "No sound.  Any ideas"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by carlito-b on 2009-06-03
Firstly I'm an absolute newbie so have some patience please ;)

I've installed ubuntu and everything works fine except I don't get any sound whatsoever.  I have an m-audio fast track external sound card.
I've tried a bunch of commands, installed new drivers and raised the levels on gnome alsa mixer but nothing seems to work.
I'm honestly at my wits end with this.

Can anyone help?

---

### Post by halitech on 2009-06-03
I'm assuming that since you say external its usb. whats the output of
```
lsusb
```

---

### Post by carlito-b on 2009-06-03
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 003 Device 002: ID 0763:2010 Midiman M-Audio Fast Track
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have my mouse in the usb aswell

---

### Post by halitech on 2009-06-03
ok, whats the output of
```
aplay -l
```

---

### Post by carlito-b on 2009-06-03
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



I appreciate you taking the time to help btw

---

### Post by gn2 on 2009-06-03
What version of Ubuntu are you using, is it 9.04?

Have you tried using the Pulseaudio configuration utility to set the desired soundcard and unmuted the volume sliders?

---

### Post by halitech on 2009-06-03
ok, well the hardware looks fine as far as being detected. What audio files are you trying to play?

welcome and thats what we are here for, to help others.

---

### Post by carlito-b on 2009-06-03
> **gn2 said:**
> What version of Ubuntu are you using, is it 9.04?

Have you tried using the Pulseaudio configuration utility to set the desired soundcard and unmuted the volume sliders?

yes it's 9.04

I've chosen the soundcard through system -> Preferences -> sound
and unmuted the sliders in gnome alsa mixer

---

### Post by carlito-b on 2009-06-03
> **halitech said:**
> ok, well the hardware looks fine as far as being detected. What audio files are you trying to play?

welcome and thats what we are here for, to help others.

I've tried vlc media player and youtube.

---

### Post by halitech on 2009-06-03
did you install the ubuntu-restricted-extras?
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by carlito-b on 2009-06-03
no, doing it now

---

### Post by carlito-b on 2009-06-03
ok going to reboot and see if IU've had any luck.

nope still quiet.  Guess I just keep trying to find what it is

Don't know if anyone can make sense of this but when I click test next to my soundcard name it says:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

### Post by carlito-b on 2009-06-03
great.
I tried some fixes and now it says no soundcards found. I give up

---

### Post by Sealbhach on 2009-06-03
Don't give up just yet, there's some good suggestions in this thread:

[http://ubuntuforums.org/showthread.php?t=769822](http://ubuntuforums.org/showthread.php?t=769822)

It looks like the module (driver) you need is snd-usb-audio so to load that module copy and paste this in a terminal:

```
sudo modprobe snd-usb-audio
```See if that makes any difference.

.

---

### Post by eMJayy on 2009-06-03
Don't know if this will help but I think it's worth a try.

Try enabling full user rights to your user account. Not all user rights for USB devices are enabled by default. This might have something to do with your USB sound card being detected by not working. 

Go to System > Administration > Users and Groups

Select your user name and click on "Unlock"

It will request your password

Then click on Properties then click the tab "User Privileges" 
Tick all the check boxes in the window. 
Restart your PC.

---

### Post by carlito-b on 2009-06-04
> **Sealbhach said:**
> Don't give up just yet, there's some good suggestions in this thread:

[http://ubuntuforums.org/showthread.php?t=769822](http://ubuntuforums.org/showthread.php?t=769822)

It looks like the module (driver) you need is snd-usb-audio so to load that module copy and paste this in a terminal:

```
sudo modprobe snd-usb-audio
```See if that makes any difference.

.

doesn't do anything when I put it in the terminal

---

### Post by Sealbhach on 2009-06-04
> **carlito-b said:**
> doesn't do anything when I put it in the terminal

OK, you won't see it do anything, but what that command does is load up the driver (module) so hopefully now your soundcard should be recognised.

.

---

