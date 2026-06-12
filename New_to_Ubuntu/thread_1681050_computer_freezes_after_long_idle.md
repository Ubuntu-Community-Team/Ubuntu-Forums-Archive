---
title: "computer freezes after long idle"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by Unguidedone on 2011-02-03
If i leave my computer on over night the computer freezes and becomes non responsive.  This also happens if I lock my computer down.  But I have noticed that if i have no applications running the odds for a freeze is less.  I know its not my motherboard since its new and less then a year old.  Any suggestions on what is causing this issue?

---

### Post by TechWiz2100 on 2011-02-03
Probably an ACPI issue with sleep.

Try changing settings in System > Preferences > Power Management to disable sleep, standby, hibernate and the like and leave it on overnight again.

If that solves the issue then look for power management issues with your cpu/chipset.

Oh and you wont be able to lock/standby until you actually solve the issue.

---

### Post by daniell59 on 2011-02-03
I would test the memory. Make sure that the voltages and the timings
 are set correctly in the BIOS.

---

### Post by Unguidedone on 2011-02-04
> **TechWiz2100 said:**
> Probably an ACPI issue with sleep.

Try changing settings in System > Preferences > Power Management to disable sleep, standby, hibernate and the like and leave it on overnight again.

If that solves the issue then look for power management issues with your cpu/chipset.

Oh and you wont be able to lock/standby until you actually solve the issue.


i disabled the lock/standby and it seems to have worked but just to be sure im going to do a memory test thanks for the help XD

---

### Post by tanpopo_chan on 2011-03-16
I had the same problem and this is how I fixed mine...

I want to start off by saying that I have an HP Pavillion dv6-2145es with an ATI Mobility Radeon HD 4650, ATI M96 Chipset, and an AMD Turion II Dual-Core Mobile M520 and I'm running Ubuntu 10.10 Maverick Meerkat x64.

This route fixed my problem, but keep in mind that freezing and hangs are very difficult to pinpoint. I suggest you read the wiki page on hangs, lockups, and freezes. It helped me figure out what caused my freezing and helped me find a solution.
- [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)
- [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

-------

First, I disabled the proprietary drivers by going to *System -> Administration -> Additional Divers* and, after, I installed fglrx manually. 
You can find a guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

-------

Second, I turned off acpi.

[I]1) In a terminal type
```
sudo gedit /boot/grub/grub.cfg
```

2) Find the option GRUB_CMDLINE_LINUX_DEFAULT and add acpi=off. For example, mine is
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

3) Reboot.[/I]

-------

Third, I followed this person's suggestion, since he seemed to have the same problem as me.
[http://ubuntuforums.org/showthread.php?p=10567976](http://ubuntuforums.org/showthread.php?p=10567976)

[I]1) Check proper installation of kernel headers with
```
sudo apt-get install linux-headers-$(uname -r)
```

2) Install the fglrx driver
```
sudo apt-get install fglrx
```

3) Select fglrx (auto mode) to use, selection for me was 0
```
sudo update-alternatives --config gl_conf
```

4) Then:
```
sudo ldconfig
```
```
sudo update-initramfs -u
```

config xorg
```
sudo aticonfig --initial
```[/I]

-------

Fourth, and final step, I followed this man's advice since during different tests, I noticed my problem was the vbetool causing problems. [http://ubuntuforums.org/showthread.php?t=1133319](http://ubuntuforums.org/showthread.php?t=1133319)
```
sudo mv /usr/sbin/vbetool /usr/sbin/vbetool.old
```

---

### Post by rosencrantz on 2011-03-16
Knowing the computer's model might help ;-) I know USB3 modules can interfere with hibernation and suspend, check the respective paragraphs e.g. in this howto:
[http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)

cheers,
rosencrantz

---

