---
title: "Laptop Speakers just quit working...."
date: 2010-03-28
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-03-28
I have a Dell XPS M1330 and Ubuntu 9.04 64bit.  All of a sudden, my laptop speakers quit working.  There is no sound and when I log off I have a system beep now.  I have everything set to automatically detect for the sound settings.  I did not make any changes or updates recently either.  Any ideas?  I supposed I can boot into Vista (shudder), to see if the audio is working there to see if it is hardware related or now...Does anybody have any ideas?

And no, it is not muted :-)

---

### Post by nemilar on 2010-03-28
Have you tried rebooting and seeing if the problem persists?

What happens in Vista?  Does it work there?

---

### Post by spartan_87 on 2010-03-28
My speakers quit working the other day when I did some updates through update manager. I found out it was the devicekit-disks package update that did it so I reverted it back to the older version and I got my sound back.

But you said you didn't do any updates, so Im not sure if thats your problem.

Have you installed any new software lately? 

Its strange they would just stop working all of a sudden. Usually an update or some other software might break it, like what happen to me.

---

### Post by readycarpenter on 2010-03-29
it could be as simple as the pcm volume is down all the way

---

### Post by NightwishFan on 2010-03-29
Run this command to check the volume.
```
alsamixer -c0
```

---

### Post by linuxus95 on 2010-03-29
Most likely, the alsa mixer is muted. The GUI way to fix this: right click the sound, select properties make sure that both the mixer and the main volume are on max. Another possibility is that the wrong hardware input/output is selected. To check that, see the hardware section in the main menu and see if the right options are selected. If you don't know, try playing around with different options (try either Analog Duplex or Digital Duplex) and see if either of them works.
 
Good luck :)

---

### Post by x C0MMAND0 x on 2010-03-29
Thank you for all of the replies!  Turns out the PCM volume was all the way down.  I was able to turn it up by running alsamixer from termnial.  By the way, what exactly is PCM volume?  I wonder how it got turned down, pretty odd. 

Thank you for the help!

---

