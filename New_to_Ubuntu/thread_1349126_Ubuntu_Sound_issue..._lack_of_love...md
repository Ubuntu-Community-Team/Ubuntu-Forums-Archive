---
title: "Ubuntu Sound issue... lack of love.."
date: 2009-12-07
forum: New to Ubuntu
---

### Post by bcdailey on 2009-12-07
Hello Forums.

So, I had very much liked the sound of Ubuntu.. the idea of ubuntu.. the look of ubuntu.. the goals of ubuntu..adn the philosophy of ubuntu.. I was even prepared to attempt to learn the new system and figure out how to make the switch to a whole mess of new programs... but I can't seem to get it to work enough to begin to play with it. 

I installed Hardy Heron on my primary machine as a dual-boot setup.. and all seemed pretty well, but I couldn't make the sound work. I tried to fiddle with it..and even tried installing new drivers via tutorial.. updating this and that, running a dozen or so terminal commands that I can't recall.. and even had a friend who turned me on to linux take a look.. and.. nada. So, I gave up on it for a while and decided that I had other things I had to do, and maybe that sound card just wasn't meant to be.

This past weekend I decided I really did want to learn linux though, and dug out a slightly older laptop that wasnt used for anything else and decided to dedicate it the cause. Everything about the two machines is entirely different.. imagine my surprise when they had the exact same problem. If Ubuntu wasn't obviously a popular and widely supported operating system, I'd begin to wonder if it had the capacity to produce sound.

I've attempted to find a fix on this machine myself, but the majority of things reference options I either don't have, or don't understand how to perform. I'd like to learn linux, but I feel a bit like I'm attempting to learn first aid but before I can progress, I need to perform open heart surgery.

For reference, the results of the first two steps in the audio troubleshooting guide 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
brooksd@brooksd-laptop:~$ sudo adduser brooksd sound
adduser: The group `sound' does not exist.

I beseech you, oh great ubuntu community.. heeeelp

---

### Post by Anuovis on 2009-12-07
Is it just a typo or did you really installed Hardy Heron? It is Ubuntu 8.04, released on April of 2008... Why not 9.04 or 9.10?

---

### Post by bcdailey on 2009-12-07
> **Anuovis said:**
> Is it just a typo or did you really installed Hardy Heron? It is Ubuntu 8.04, released on April of 2008... Why not 9.04 or 9.10?

That was on the other machine.. and my last attempt..and yes, i attempted to upgrade it, which never did fix the problem. The laptop im on now, and the information posted above is for 9.10

---

### Post by Tku on 2009-12-08
Hello!!!

I googled your problem and i found a solution here on Ubuntu Forums :o. I think it will solve the problem since its the same Playback device.

Here is the link: [http://ubuntuforums.org/showthread.php?t=161193](http://ubuntuforums.org/showthread.php?t=161193)

Good luck. :D

---

### Post by The_Pirate_King on 2009-12-08
Different distrobutions seems to react differently with different machines.  Try 9.04 or 9.10 on your main machine and see if that gets you anywhere, you could have just had an unlucky coincidence. 
I myself had sound issues on 8.04. 

Or if you want to move away from Ubuntu entirely, try Linux Mint, it is similar to Ubuntu but has a focus on making things work out of the box.  There is a good chance it will fix your sound issues. 
[http://www.linuxmint.com/](http://www.linuxmint.com/)

---

### Post by bcdailey on 2009-12-08
> **Tku said:**
> Hello!!!

I googled your problem and i found a solution here on Ubuntu Forums :o. I think it will solve the problem since its the same Playback device.

Here is the link: [http://ubuntuforums.org/showthread.php?t=161193](http://ubuntuforums.org/showthread.php?t=161193)

Good luck. :D


I'm attempting the solution shown..and at the risk of sounding like a complete invalid, how do i uncheck the external box? the sliders respond to directional arrows.

---

### Post by bcdailey on 2009-12-08
I wound up getting a GUI version of alsamixer ... problem solved..

and.. it works! huzzah!

Thank you!

---

### Post by Tku on 2009-12-08
No problem, we are here to help each other.

Have a nice stay!!!. :)

---

### Post by Tku on 2009-12-08
Oh and by the way, for the no GUI version of alsamixer just press M on your keyboard and thats all.

I didnt now how to do it either and a few min ago i dicover the way to do it. Thanks to you i know more than an hour ago.

---

