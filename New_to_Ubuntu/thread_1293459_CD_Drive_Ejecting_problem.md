---
title: "CD Drive Ejecting problem"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by landy rover on 2009-10-17
Hi everyone

I am new to ubuntu (currentley running 8.10) i seem to have a diffuculty with my dvd drive Every time i got to Computer and Right click And say eject it ejects my dvd drive perfect but within 2 seconds it just goes back into the drive without doing anything to it...:confused:
but when i eject it for the second time the drive stays out it is just very strange can somebody please help me

I think ubuntu and the whole linux idea is very cool OPEN SOURCE IS AWESOME

---

### Post by CaptainMark on 2009-10-17
does it do the same thing if you pop this into the terminal ```
sudo eject /dev/cdrom
``` depending on how new you are: terminal is accessed by clicking applications > accessories >terminal

---

### Post by mc4man on 2009-10-17
Interesting that your having that issue in 8.10 which was something that did occur but was fixed (or at least for most people

the 'fix' was an update to udev as seen first here in 'proposed'

> udev (124-9) intrepid-proposed; urgency=low

  * Add debian/patches/01-cdrom-vol_id-probing.patch: Do not run vol_id on
    optical drives if there is no medium in the drive. Doing so open()'s the
    drive without O_NONBLOCK which closes the tray. Patch backported from
    upstream GIT (released in version 126). (LP: #283316)

 -- Martin Pitt <martin.pitt@ubuntu.com>  Mon, 03 Nov 2008 19:02:15 +0100


Maybe search udev in synaptic and see if your version is udev (124-9ubuntu0.2)

If not then update it.

If it is (124-9ubuntu0.2), then you could try right clicking on the package and "Mark for Reinstallation" and  click apply

(**Don't Remove**, just re-install

---

### Post by 3rdalbum on 2009-10-17
Run all your system updates to fix this problem. Also bear in mind that Ubuntu 8.10 reaches End Of Life in six months time; maybe you should consider installing Ubuntu 9.10 when it comes out at the end of the month?

---

### Post by ikisham on 2009-10-17
Yes, that's an Intrepid bug. When I used it this issue was never solved. Newer version of Ubuntu don't have it.

---

### Post by LewRockwell on 2009-10-17
> **3rdalbum said:**
> Run all your system updates to fix this problem. Also bear in mind that Ubuntu 8.10 reaches End Of Life in six months time; maybe you should consider installing Ubuntu 9.10 when it comes out at the end of the month?

or you could try out 9.04 since more of it's bugs have been smashed

.

---

### Post by landy rover on 2009-10-17
Thank you 

Thanx everyone who helped me with this problem 
but i tried to update the udev in synaptic manager and didn't help 
but I'm going to wait for ubuntu 9.10 then going to upgrade anyway

But thanx anyway

---

### Post by ikisham on 2009-10-17
Oh, I forgot to say: when you eject the cd/dvd press quickly the eject button on the cd writer when it starts to close and it will open and stay there.

---

