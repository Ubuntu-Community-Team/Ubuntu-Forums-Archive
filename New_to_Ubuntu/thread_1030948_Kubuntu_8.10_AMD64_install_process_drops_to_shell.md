---
title: "Kubuntu 8.10 AMD64: install process drops to shell"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by thomas_r2 on 2009-01-04
Trying to install Kubuntu 8.10 AMD64 and running into a frustrating problem. After electing to do a fresh install, the Kubuntu splash and progress bar appears, then after some time the splash disappears and I am dropped to a shell prompt. There are no apparent errors, just some text saying "Linux Ubuntu 2.6.27-7 generic #1 SMP .... x86-64" along with a few general instructions like how to use man sudo-root, etc. Then I am dumped in /home/ubuntu.

The burned CD checks out okay, but just in case I downloaded and burned a second copy - same result.

The machine is an Asus M3A78-Pro mainboard, Phenom 8750, 8GB OCZ PC8500, with the primary display plugged into an Asus EAH3450 PCI-E card. This gear is an upgrade from a previous rig (MSI RS482-M4 with Opteron 170 and ATI X800XL) and that hardware manifested the exact same problems.

Any clues? I tried "startX" and a handful of the other shell commands I happen to know, but no joy.

---

### Post by The Joe on 2009-01-04
I'm completely unsure - but try pressing Ctrl+Alt+F7 when you end up in the Terminal. That _MIGHT_ work, if it doesn't it's the X Server dying and I know nothing about that.

---

### Post by thomas_r2 on 2009-01-04
Ctrl+Alt+F7 clears the contents of the text screen, leaving a blinking cursor in the top left

If I hit Ctrl-Alt-Del, I get back to the Kubuntu splash and progress bar, and eventually a message "remove CD and hit enter to reboot system"

---

### Post by RomeReactor on 2009-01-04
Hi. After you're dropped to the console, try:
```
sudo /etc/init.d/kdm start
```
or:
```
sudo /etc/init.d/kdm restart
```

If your motherboard has integrated graphics, you can try to perform the installation using that rather than the PCIe card, and switch to the dedicated card after the system is correctly installed.

---

### Post by thomas_r2 on 2009-01-04
sudo /etc/init.d/kdm restart generates the following messages:

Stopping K Display Manager: kdm
Starting K Display Manager: kdm

... but nothing (aside from this highly informative text) actually appears onscreen.

I configured the mainboard BIOS to use onboard graphics as the primary display and tried installing. This time instead of dropping to shell, the display would flicker every 5-10 seconds and the monitor would display "No Signal" periodically ... almost looks as if some kind of service is trying to repeatedly restart.

I should note that an old Knoppix CD (5.1.1) boots up on this machine without missing a beat ... and I installed OpenSUSE 10.x in the past (on the previous hardware) without difficulty.

---

### Post by thomas_r2 on 2009-01-05
I can now confirm that OpenSUSE 11.1 installs seamlessly on this hardware. Since this machine is intended to be a host/testbed for Virtualbox network clustering, I am considering sticking with Suse at this point ... maybe I'll try Ubuntu/Kubuntu as a virtual machine sometime later.

---

### Post by jiangshi on 2009-01-05
> **thomas_r2 said:**
> I can now confirm that OpenSUSE 11.1 installs seamlessly on this hardware. Since this machine is intended to be a host/testbed for Virtualbox network clustering, I am considering sticking with Suse at this point ... maybe I'll try Ubuntu/Kubuntu as a virtual machine sometime later.

I have the same problem with an ASUS A8N-E MB and AMD 64bit Athlon processor. It runs SuSE 64bit just fine, but I can't even make it all the way through the install with the 64 bit Ubuntu 8.10 desktop version. I haven't tried the server version. Since this machine is my network server, I leave SuSE on it since it works without a hiccup, and if it ain't broke, don't fix it.

I have another machine that I am playing with the 32 bit server version of Ubuntu 8.10.

~jiangshi

---

