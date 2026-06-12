---
title: "BIOS Setting -&gt; USB Emulation"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Chrissd on 2011-04-16
Hi all, had problems with my wife's Inspiron M501R not booting with any of the new Linux headers since 10.04, and just hanging on boot. Didn't seem to crash, just not boot. Turning ACPI(?) off seemed to fix it, but disabled many features like the computer actually switching off when shutting down. You had to manually hit the power off once the computer had shut down as well as other annoying things.#

I read that someone set the "USB Emulation" to off in BIOS to get Ubuntu to install and tried it. This fixed the problem and Ubuntu now boots happily.

Problem is, I have no idea what this is. I've googled it and the [Dell Support page](http://support.dell.com/support/edocs/systems/opgx110/ens/ug/setupopt.htm) says:
> 
USB Emulation

USB Emulation determines whether the system's basic input/output system (BIOS) controls Universal Serial Bus (USB) keyboards and mice. When On is selected, the BIOS controls USB keyboards and mice until a USB driver is loaded by the operating system. When Off is selected (the default), the BIOS does not control USB keyboards and mice, although they function during the boot routine. Set USB Emulation to Off if you are using a PS/2-compatible keyboard and mouse.

My wife's Inspiron is a laptop and has no USB keyboard and mouse loaded as it's obviously built into it. Are there any impending problems I should look out for or is this the solution we've been waiting for.

Many thanks in advance!

---

