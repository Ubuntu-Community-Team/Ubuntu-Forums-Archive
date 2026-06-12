---
title: "Help for idiot again"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by mjhall29 on 2011-05-22
I have installed 11.04 64bit on Toshiba T230-10j laptop. (duel boot with windows 7 hoping to get rid of windows eventually) 
system starts to boot, loads, then stops before finished. if i load it in safe graphics mode all works well but cant use things like google earth due to low res setting. 
i had the same when i loaded it onto a HP 64bit machine but after an update all was well.
as far as i can tell it is the graphics driver for the i3 processor, but i don't know enough about Linux to compile and install the Intel drivers on there Linux support page. they say the Linux distributor will have the binary code but again i don't:confused: know enough to decide what i software i need?
Please help as i do not want to go back to W7.

---

### Post by crispy_420 on 2011-05-22
Any reason you went with 64bit? More than 4GB RAM?

---

### Post by mjhall29 on 2011-05-23
> **crispy_420 said:**
> Any reason you went with 64bit? More than 4GB RAM?

have 4GB of ram went for 64 bit because thats what the machine is. why should i have installed 32 bit would that solve my problem?

---

### Post by Paqman on 2011-05-23
> **mjhall29 said:**
> why should i have installed 32 bit would that solve my problem?

No, it sounds like your problem is graphics. The drivers for your Intel card should be pre-installed though, so there's no need to compile anything. Normally Intel graphics will just work, i'm not sure why your machine seem to be acting up.

---

### Post by wildmanne39 on 2011-05-23
> **mjhall29 said:**
> I have installed 11.04 64bit on Toshiba T230-10j laptop. (duel boot with windows 7 hoping to get rid of windows eventually) 
system starts to boot, loads, then stops before finished. if i load it in safe graphics mode all works well but cant use things like google earth due to low res setting. 
i had the same when i loaded it onto a HP 64bit machine but after an update all was well.
as far as i can tell it is the graphics driver for the i3 processor, but i don't know enough about Linux to compile and install the Intel drivers on there Linux support page. they say the Linux distributor will have the binary code but again i don't:confused: know enough to decide what i software i need?
Please help as i do not want to go back to W7.
Hi, have you went to administration then click on additional drivers to see if there is a driver for your card in there if so there might be 2 try the other one and see if that works.

---

### Post by mjhall29 on 2011-05-25
> **wildmanne39 said:**
> Hi, have you went to administration then click on additional drivers to see if there is a driver for your card in there if so there might be 2 try the other one and see if that works.

did that the only driver to show up is for WIFI

---

### Post by mjhall29 on 2011-05-25
> **Paqman said:**
> No, it sounds like your problem is graphics. The drivers for your Intel card should be pre-installed though, so there's no need to compile anything. Normally Intel graphics will just work, i'm not sure why your machine seem to be acting up.

when i go to system settings it says it is an unknown monitor?

---

### Post by Ghost|BTFH on 2011-05-25
Sorry, I'm not sure where anyone heard that Intel drivers "just work" out of the box with 11.04 but that's a horrible mistake to believe.

If you don't have ATi or nVidia, you generally aren't going to have 3D accelerated drivers.  If you don't have 3D accelerated drivers, you don't have a 3D desktop (default in 11.04) and that leaves you with 2D (ie safemode) only.

For what it's worth, ldxe works beautifully in lower end graphics and performs amazingly well.  I'd look into it.

Cheers,
Ghost|BTFH

---

### Post by wep940 on 2011-05-25
Some Intel graphics don't play well with KSM - Kernel Set Mode - in which the kernel now tries to set up your video.  It used to be you could put in i915.modeset or some such thing at boot time, but I believe it has been changed to just nomodeset.

What you need to do:

- when the grub boot menu comes up, highlight Ubuntu if not highlighted by default, then press E

- use the arrow keys to position the "cursor" to where it say "quiet splash" (hint - if that appear on a line on your screen after a line that starts with "linux", it means the line has wrapped.  Go to the start of the line after the "quiet splash" line and then press the left arrow key)

- change "quiet splash" to nomodeset

- hold down the Ctrl key and press the "+" key to boot

This is just a 1-time change to see if it works for you.  If it does, post back and we'll walk you through making the change permanent.

---

### Post by mjhall29 on 2011-05-27
> **wep940 said:**
> Some Intel graphics don't play well with KSM - Kernel Set Mode - in which the kernel now tries to set up your video.  It used to be you could put in i915.modeset or some such thing at boot time, but I believe it has been changed to just nomodeset.

What you need to do:

- when the grub boot menu comes up, highlight Ubuntu if not highlighted by default, then press E

- use the arrow keys to position the "cursor" to where it say "quiet splash" (hint - if that appear on a line on your screen after a line that starts with "linux", it means the line has wrapped.  Go to the start of the line after the "quiet splash" line and then press the left arrow key)

- change "quiet splash" to nomodeset

- hold down the Ctrl key and press the "+" key to boot

This is just a 1-time change to see if it works for you.  If it does, post back and we'll walk you through making the change permanent.

when i did this it booted into low res mode. was that what you expected?

---

### Post by mjhall29 on 2011-05-27
[QUOTE=mjhall29;10870237]when i did this it booted into low res mode. was that what you expected?
although i like this version would i be better of with an older version as its not much use in low res mode?
or should i just give up hope of getting rid of the other operating system?

---

### Post by wep940 on 2011-05-28
Well, what I would try - no guarantee here is the following:

- boot again with nomodeset in the boot line
- make sure you are connected to the internet
- click system/administration/restricted drivers (or additional drivers)
- wait for this to run - it will do a search on the net and if a driver is found it will download it and install it so it shows in the Window.  When all done, if a driver for the video shows in the screen be sure to click the box to activate it
- reboot

---

