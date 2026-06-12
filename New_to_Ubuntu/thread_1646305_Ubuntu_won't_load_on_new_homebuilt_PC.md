---
title: "Ubuntu won't load on new homebuilt PC"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by PaleoNerd on 2010-12-15
Hi all,

I just finished building a new PC and was trying to load Ubuntu onto it. I've tried both 32 bit and 64 bit both from CD and a USB drive. They both start off fine but after awhile I get this on my screen:

[IMG]http://i32.photobucket.com/albums/d37/Jeff_Matzke/IMG_0033.jpg[/IMG]

Any idea what is wrong?

---

### Post by themusicalduck on 2010-12-15
What graphics hardware are you using?

---

### Post by PaleoNerd on 2010-12-15
EVGA GeForce 240  PCI Express 2.0 512 MB DDR5

---

### Post by MooPi on 2010-12-15
Try your install with only one monitor. After install you can configure the dual setup.

---

### Post by PaleoNerd on 2010-12-15
> **MooPi said:**
> Try your install with only one monitor. After install you can configure the dual setup.

Already did that, still didn't work.

---

### Post by MooPi on 2010-12-15
Give us the system specs and more details. I have a feeling they might be needed. Also try the install option ```
noacpi
```

[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by PaleoNerd on 2010-12-15
Here are the specs:

Intel Core i5-661 3.33 GHz processor
Intel Desktop DQ57TM motherboard
8 GB OCZ DDR3 Memory

---

### Post by RedRat on 2010-12-15
Can  you boot up from the LiveCD? Does the graphics card work then correctly running from that CD?

---

### Post by oldfred on 2010-12-15
My older Nvidia works but I had to do these things, do not know if they also apply to the newest versions or not:

I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

Some with Nvida chips had to use the Generic settings:
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by sandyd on 2010-12-15
nomodeset comes into mind.
the nouveau drivers have been causing some major problems with some cards.

---

