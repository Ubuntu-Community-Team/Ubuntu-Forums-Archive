---
title: "Skype sound problem in Karmic"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by confused_person on 2010-03-12
When I open skype, it makes the sign-on noise--well, half of the sign on noise, then it sort of craps out--and then is completely silent. 

Before, it wouldn't make any noise at all, and if I made a test call it would say "Problem with audio playback". I tinkered around with the sound options and now I can make a test call that acts like it's working, but there is no sound whatsoever, not even ringing. I've tried various combinations of input/output sources and nothing is fixing this problem. Any advice? I'm on a Macbook 4,1 btw.

---

### Post by XubuRoxMySox on 2010-03-13
Grrrrr @ PulseAudio, I think. Uninstall Skype and use an older version or try installing "Skysentials" (don't think I spelled it right) from Synaptic and see if that helps.

-Robin

---

### Post by confused_person on 2010-03-14
> **dixiedancer said:**
> Grrrrr @ PulseAudio, I think. Uninstall Skype and use an older version or try installing "Skysentials" (don't think I spelled it right) from Synaptic and see if that helps.

-Robin

Robin,
Thanks! I tried both of your suggestions. What worked was actually installing the new Beta version of 2.1 from Skype's website. I no longer have any problems. Thank you! :D

---

### Post by rosegarden78 on 2010-05-05
I have Skype Beta 2.1.0.81 and the Audio In/Out still has problems.  It malfunctions.  It drops sound in the middle of the call.  Are you using 32-bit version?  I'm using the 64-bit Skype on a Ubuntu Studio Lucid Lynx 10.04 system.  Could that be the problem for me?  Or does it plague all Linux versions?

UPDATE: Wrong thread I have Lucid, but I finally found a work-around: Using Skype for Windows in VirtualBox with Windows XP.  Just add this line: none /proc/bus/usb usbfs devgid=120,devmode=664 0 0
to your /etc/fstab file, replacing 120 with your vboxusers group number, and you'll have webcam support.

---

