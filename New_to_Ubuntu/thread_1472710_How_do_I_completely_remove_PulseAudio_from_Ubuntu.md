---
title: "How do I completely remove PulseAudio from Ubuntu?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Kangaroo_Style on 2010-05-04
I keep getting this error: "Waiting for sound system to respond" when I try to click on the sound menu in preferences > sound. I am unable to change my system sound now. I still get sound, just I can't adjust the volume.

My line of thinking is that, I should completely remove everything Pulse Audio in Ubuntu. Then reinstall Pulse. And see if that would fix the problem.  What do you guys think?

---

### Post by mörgæs on 2010-05-04
Which Ubuntu version are you using?

---

### Post by Kangaroo_Style on 2010-05-04
> **mörgæs said:**
> which ubuntu version are you using?


10.04

---

### Post by emoguitarist06 on 2010-05-04
> **Kangaroo_Style said:**
> I keep getting this error: "Waiting for sound system to respond" when I try to click on the sound menu in preferences > sound. I am unable to change my system sound now. I still get sound, just I can't adjust the volume.

My line of thinking is that, I should completely remove everything Pulse Audio in Ubuntu. Then reinstall Pulse. And see if that would fix the problem.  What do you guys think?

Applications>Accessories>Terminal
$ sudo apt-get remove --purge pulseaudio

that should do it
than just 
sudo apt-get install pulseaudio if you want it back

---

### Post by Kangaroo_Style on 2010-05-04
> **emoguitarist06 said:**
> Applications>Accessories>Terminal
$ sudo apt-get remove --purge pulseaudio

that should do it
than just 
sudo apt-get install pulseaudio if you want it back


Hmm, I tried purging it. And then reinstalling Pulse. 

Still getting the error: "Waiting for Sound System to Respond"

---

### Post by mörgæs on 2010-05-05
May I guess, you upgraded 9.10 to 10.04 in stead of doing a clean install? 

If you have a .pulse directory in your home directory, does it help if you delete it and boot afterwards?

---

### Post by Kangaroo_Style on 2010-05-05
> **mörgæs said:**
> May I guess, you upgraded 9.10 to 10.04 in stead of doing a clean install? 

If you have a .pulse directory in your home directory, does it help if you delete it and boot afterwards?


Yeah I did the the upgrade from 9.10. I would have done a clean install, but I don't have an external HDD to put all my music, pictures, and other stuff on it. So the upgrade was my only option.


Yes I have tried deleting the .pulse directory and rebooting and it did not work.

---

### Post by lidex on 2010-05-05
Do 'Part A' on this page:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Also read through the appendices.

---

