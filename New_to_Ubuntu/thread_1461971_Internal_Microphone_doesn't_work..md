---
title: "Internal Microphone doesn't work."
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Kafubie on 2010-04-24
**_I guess I need some help._**
Guys I am using a HP mini 1125 netbook with Karmic.  Everything works except for the Internal Mic.  Is there someway I can get this working?  

**_GURUS OF COMPUTERS PLEASE BRING ME YOUR POWERS!_**
Thanks
-Nathan

---

### Post by Aearenda on 2010-04-24
Maybe the 1125 has the same problem as the Aspire One on Karmic - see [http://ubuntuforums.org/showpost.php?p=8405465&postcount=18](http://ubuntuforums.org/showpost.php?p=8405465&postcount=18)

---

### Post by Kafubie on 2010-04-26
I'll give this a try, I am about to do this if this doesn't work how would I uninstall the package?

Thanks for the help!
-Nathan

---

### Post by Kafubie on 2010-04-26
> **Aearenda said:**
> Maybe the 1125 has the same problem as the Aspire One on Karmic - see [http://ubuntuforums.org/showpost.php?p=8405465&postcount=18](http://ubuntuforums.org/showpost.php?p=8405465&postcount=18)

Bad news, it doesn't work.  I did remove it, so no need to tell me how to uninstall it.  

Thanks for trying!
-Nathan

---

### Post by Kafubie on 2010-04-26
**bamp!**

---

### Post by lidex on 2010-04-26
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Kafubie on 2010-04-27
**Hereyago!**
HP mini 1125(already said)  The webcam works, just to point that out there.
```
Linux nathaniel-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
```
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
Advanced Linux Sound Architecture Driver Version 1.0.20.
```
```
Codec: IDT 92HD81B1X5

```

-Nathan
:confused:

---

### Post by Arla on 2010-04-27
> **Kafubie said:**
> **_I guess I need some help._**
Guys I am using a HP mini 1125 netbook with Karmic.  Everything works except for the Internal Mic.  Is there someway I can get this working?  

**_GURUS OF COMPUTERS PLEASE BRING ME YOUR POWERS!_**
Thanks
-Nathan

Have you tried Backports?

Y450 Mic didn't work in Karmic out of the box, but after installing

linux-backports-modules-alsa-2.6.31-14-generic

It worked (or whatever the latest version of the kernel is in Karmic, as a side note, mic works just fine out of the box (in my Y450) on Lucid, so it MAY be worth waiting till the end of the week and trying Lucid (or try Lucid Live CD?)

---

### Post by lidex on 2010-04-27
Yes, install the backports. Go here to do so:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Alternately, you can do an alsa upgrade - the link is in my sig. Once done, use alsamixer to check/set levels. 
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.

---

### Post by pihbar on 2010-04-27
There is a similar bug being squashed at the moment. Maybe this will help you, as well. Or you can report a new bug!
[https://bugs.launchpad.net/bugs/477226](https://bugs.launchpad.net/bugs/477226)

---

