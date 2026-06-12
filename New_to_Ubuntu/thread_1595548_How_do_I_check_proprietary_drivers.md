---
title: "How do I check proprietary drivers?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Debra.S on 2010-10-13
I'm going to include everything I can with this, but please be patient as I'm slowly learning Ubuntu.

This started as an upgrade issue - [http://ubuntuforums.org/showthread.php?t=1595475](http://ubuntuforums.org/showthread.php?t=1595475)

I was reading in the pocket guide, and decided to start with checking the video drivers.  Except now in 10.10, I don't have a 'hardware drivers' option under system->admin.  I do have an option for 'additional drivers' which looks to be the same thing... but the only thing it brings up is the Broadcam STA driver.

I'm on a Dell Inspiron 15n that was new in Sept. 09, and upgraded twice now.  I can try to give more information if you tell me how to find it.

Thanks.

---

### Post by pmlxuser on 2010-10-13
likely the video driver has been opened and thus its no longer third party.

---

### Post by Debra.S on 2010-10-13
> **pmlxuser said:**
> likely the video driver has been opened and thus its no longer third party.

Ok well, I was able to find the information on my disk drive, and it does have the latest firmware...

That still leaves me completely lost though as to why it won't read disks.  The information on the drive is as follows:

Optiarc DVD +-RW AD-7560S
Firmware version SD05

Any ideas where to go from here?  It's kind of frustrating not having my only disk drive not working.

Thanks.

---

### Post by pmlxuser on 2010-10-13
have you tried restarting your machine with the CD or DVD inside the optical drive; it is rumoured that it works sometimes for those with similar problems

like this one 
[http://forums.linuxmint.com/viewtopic.php?f=49&t=49518&start=0](http://forums.linuxmint.com/viewtopic.php?f=49&t=49518&start=0)

---

### Post by Debra.S on 2010-10-13
I'll try that, but in the meantime, here's something else...

I tried to run a benchmark test of the drive, and got this error: Error benchmarking: helper exited with exit code 1: Device /dev/sr0 is too slow to benchmark

I was reading up about Medibuntu, and ran the commands here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) but it didn't help.

I just feel like I'm stubling through this - thanks for taking the time to help me.

Ok starting the computer with the disk in the drive didn't help.  Now I get "cannot read from resource" when using it.  Tried a benchmark test on the drive again, and this time got this error: Error benchmarking: helper exited with exit code 1: Error reading 104857600 bytes at 104857600 from /dev/sr0 when guesstimating buffer size: Input/output error

---

### Post by Debra.S on 2010-10-13
Alright, well, if anyone stumbles upon this with a similar video issue, I'll post what I did.

VLC player is working fine now, and I was able to run a benchmark, but I'm still not having luck with Movie Player.  However, VLC is my preferred player, so I'm just going to be happy with the results for now.

I went to: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and ran the commands, then went into the package directory and it found some packages that needed upgraded.  (There hadn't been any before I ran the Medibuntu commands.) Installed those and rebooted, and VLC is working fine.  

So, I guess I'm learning.

---

### Post by AndyM3 on 2010-10-13
You should mark the thread solved if you figured it out. It's under "thread tools".

---

### Post by donarntz on 2010-10-13
When I try benchmarking I get the same error on both my pata cd/dvd drives, and my sata cd/drive throws an error that it's "too slow".  Also, the playback of a dvd is jittery/shaky with movie player but fine on vlc.  These errors all seem to be new with maverick.  Anyone else?

---

### Post by Mark Phelps on 2010-10-14
Donarntz: This thread has already been solved.  Please don't hijack it for a new problem on your PC.  Please start your own thread, instead.

---

### Post by donarntz on 2010-10-14
Well it seems to be the same problem the other person is having, and it isn't marked "solved".  But thanks for the help...

---

### Post by Debra.S on 2010-10-14
This issue wasn't solved.  In fact, the issue with my optical drive got so bad that I ended up restoring my computer to factory settings.  No one would really help me and no one else seemed to be having or ever had the problems I was having.  I have a more recent post about it from today.

I'm running 8.10 right now, which is what my laptop came installed with, and having no problems with reading from the optical drive, nor mounting isses, etc.  Going to upgrade to 10.04 overnight and then start updating firmware and go from there.

I'm sorry I don't have an actual solution for you, but check my other post (from today) and if you're having the same issues, I suggest going back to a previous version.  PITA but everything is working fine again.

Good luck.

---

### Post by srlake314 on 2011-04-06
Yeah VLC DOESNT work for me at all, I get several errors about unable to read.  I dont have that pc up right now because it's been kind of stressful trying to get HD4770 working properly with Wow and now just playing DVDs out of the case.  Movie Player does work now, but the film is jittery, but it does play, however again VLC doesnt work.

I have done that one website about setting up and it's alot of processes and I did them all, but to no avail.

I just dont know about Ubuntu, too much figuring stuff out just to get basic features to run.

---

