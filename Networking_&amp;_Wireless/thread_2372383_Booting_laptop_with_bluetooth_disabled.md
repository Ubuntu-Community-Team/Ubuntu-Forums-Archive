---
title: "Booting laptop with bluetooth disabled"
date: 2017-09-24
forum: Networking &amp; Wireless
---

### Post by TuxManRemove on 2017-09-24
Hello,

How can I disable bluetooth on boot my laptop?

I try with:
sudo rfkill block bluetooth
in file
/etc/rc.local

but nor work...

The wifi card is Intel with bluetooth integrated.

I search solutions, but not work:
[https://ubuntuforums.org/showthread.php?t=1585069](https://ubuntuforums.org/showthread.php?t=1585069)

Thanks,

---

### Post by jeremy31 on 2017-09-24
Do you plan on using bluetooth?  I know a way that will disable it until a file is changed and a reboot is done.  Post results for ```
lsusb
```

---

### Post by ajgreeny on 2017-09-24
If you are never going to use b/t you can remove the bluetooth package from the system but I suggest you avoid removing other packages such as libbluetooth3 as it will take other things with it.

---

### Post by Autodave on 2017-09-25
Couldn't they just go into Settings -> Session & Startup and disable it?

---

### Post by ajgreeny on 2017-09-25
I don't think it's that simple if using Ubuntu with unity as only applications you have personally added to the autostart list show.

I am sure there must be a way to do this in a simpler way, and you can try installing Boot-Up-Manager (bum) and stopping it running using that.

---

### Post by jeremy31 on 2017-09-25
I use a udev rule to disable my internal bluetooth when I want to test USB bluetooth devices or if I just don't want bluetooth running

---

