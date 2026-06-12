---
title: "Canon camera"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Diametric on 2010-01-20
I just purchased a canon Power Shot sx110 is...and the canon website does not have drivers for Linux.  Am I screwed? I plugged the camera in and the OS locked up and I had to do a hard reboot.  Hopefully, there is something that can be done.  Thanks in advance for the help.

---

### Post by ajgreeny on 2010-01-20
I seem to remember reading in the past that canon cameras were a problem in ubuntu, and linux in general.  The easiest way to proceed is probably to not bother searching too long and hard, or even if you do continue searching, I still suggest you get a cheap card reader to download photos.  Not only will it be a lot faster, but it will also not need power to the camera to do it.

---

### Post by Simian Man on 2010-01-20
My wife has a Cannon Powershot A1100 (I think) and it works just fine with my laptop running Fedora 12. I just plugged it in and F-Spot opened with all of our photos.

It's especially odd that just plugging it in locked the OS.  I don't think I've ever had a device do that.  Does that happen every time?

---

### Post by tea for one on 2010-01-20
> **Diametric said:**
> I just purchased a canon Power Shot sx110 is...and the canon website does not have drivers for Linux.  Am I screwed? I plugged the camera in and the OS locked up and I had to do a hard reboot.  Hopefully, there is something that can be done.  Thanks in advance for the help.

I have a Canon IXUS 80 IS and this camera is supported by Digikam software available via Synaptic.

I had a quick look at the Digikam list of Powershot cameras and both the SX100 and the SD110 are listed. I imagine your camera is a slightly newer model. 

My Digikam software is version is 0.9.3 for Ubuntu 8.04 and I suspect that there is a newer version for Karmic. The later Digikam versions may well list your camera.

Failing that, I agree with ajgreeny that the failsafe solution is to transfer the photos using a card reader.

Good luck

---

### Post by Diametric on 2010-01-20
Yes, it locked up several times.  So, after some research, there is are 2 packages that can be found in Synaptic called "libgphoto2" and "camera.app" after i stalled both of these, Ubuntu recognized the camera and an app allowed me to DL my pics.  No muss no fuss and deff no MS.

cheers.

---

### Post by Simian Man on 2010-01-20
> **Diametric said:**
> Yes, it locked up several times.  So, after some research, there is are 2 packages that can be found in Synaptic called "libgphoto2" and "camera.app" after i stalled both of these, Ubuntu recognized the camera and an app allowed me to DL my pics.  No muss no fuss and deff no MS.

Nice, glad it's working for you now :).

---

### Post by lisati on 2010-01-20
> **Diametric said:**
> Yes, it locked up several times.  So, after some research, there is are 2 packages that can be found in Synaptic called "libgphoto2" and "camera.app" after i **in**stalled both of these, Ubuntu recognized the camera and an app allowed me to DL my pics.  No muss no fuss and deff no MS.

cheers.

Fixed. I think you meant **installed** - stalling something poses a risk of lockup.

---

