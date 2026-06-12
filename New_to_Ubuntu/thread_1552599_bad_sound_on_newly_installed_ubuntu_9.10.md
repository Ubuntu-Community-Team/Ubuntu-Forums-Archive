---
title: "bad sound on newly installed ubuntu 9.10"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by grunt1962 on 2010-08-13
Newbie and rookie here. I have a old Dell dimension 4550 that had windows xp installed when I purchase it. Now that I see the "light" xp is gone but now my audio is terrible. Lots of stactic. Can someone walk me through getting better sound? I tried the preferences in the sound category and no avail. Please help this rookie.....

---

### Post by Jazzy_Jeff on 2010-08-13
Can you give us the specs of your system and or model number. Also, just wondering why you didn't install the latest version of Ubuntu which is 10.04.

---

### Post by lidex on 2010-08-13
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by grunt1962 on 2010-08-14
> **Jazzy_Jeff said:**
> Can you give us the specs of your system and or model number. Also, just wondering why you didn't install the latest version of Ubuntu which is 10.04.
  
The tag on back of the tower is.....D5TG721... I guess this is the model number? I  can't find my  specs. Where do I start?....rookie here...  ubuntu 9.10 was available at the time

---

### Post by grunt1962 on 2010-08-14
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
  a play-l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
``````
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

uname -a
Linux user-desktop 2.6.31-22-generic #61-Ubuntu SMP Wed Jul 28 01:57:06 UTC 2010 i686 GNU/Linux
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 1: CS46xx - Rear [CS46xx - Rear]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CS46xx [Sound Fusion CS46xx], device 3: CS46xx - Center LFE [CS46xx - Center LFE]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #3
 dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.20+dfsg-1ubuntu5                       ALSA driver configuration files
ii  alsa-utils                                 1.0.20-2ubuntu6                            ALSA utilities
ii  bluez-alsa                                 4.51-0ubuntu2                              Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.25-2ubuntu1.2                         GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-5                                   Enlightened Sound Daemon (ALSA) - Shared lib
ii  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                            Simple DirectMedia Layer (with X11 and ALSA 

head -n 1 /proc/asound/card*/codec#*   ....nothing when this is entered

dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel' nothing with this is entered also

---

### Post by simosx on 2010-08-14
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Hi lidex,

The Ubuntu Wiki for sound troubleshooting has been updated,
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

It shows a new way to collect sound information to help in debugging. (I used to suggest people to get alsa-info.sh, but it's deprecated as well).

So, I think the best to ask users to do is perform those steps at 
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
to collect as much as possible from their system and auto generate a bug report. Then, provide the link to launchpad here.

In other words, users of Ubuntu 10.04 (or newer) should now run
[FONT="Courier New"]
ubuntu-bug audio[/FONT] 
and follow the wizard. Finally, they should post here the bug report URL.
If sound does not work by default, then it's a bug and requires a bug report.

---

### Post by lidex on 2010-08-14
> **simosx said:**
> Hi lidex,

The Ubuntu Wiki for sound troubleshooting has been updated,
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

It shows a new way to collect sound information to help in debugging. (I used to suggest people to get alsa-info.sh, but it's deprecated as well).

So, I think the best to ask users to do is perform those steps at 
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
to collect as much as possible from their system and auto generate a bug report. Then, provide the link to launchpad here.

In other words, users of Ubuntu 10.04 (or newer) should now run
[FONT="Courier New"]
ubuntu-bug audio[/FONT] 
and follow the wizard. Finally, they should post here the bug report URL.
If sound does not work by default, then it's a bug and requires a bug report.

Copy that.
**This** problem is probably fixed with an alsa-upgrade via the link in my sig as OP's version is older. Also make sure settings are not too high in alsamixer:
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by grunt1962 on 2010-08-14
When I enter alsamixer I get card- sound fusion c546xx,:confused: Rookie needs help bad....This link is helping somewhat...
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

uname -r.....I guess I'm running the right kernel(?) because my results start with" 2.6.31"

---

