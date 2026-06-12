---
title: "Lucid Lynx eeepc 1005HA fn Keys"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by I_MELT_FACES on 2010-07-27
Hey, 
I am a noob at Linux, Installed this past weekend. I need to get my fn keys to work. Particularly I want to be able to turn on/off my wireless card with a key combination (fn+f2) Because I am going to travel and want to use less power, so that my battery life will last longer. Can anyone help me? Also are there any other tips other than the power management (spin down disk, dim laptop screen) options to help increase battery life? In windows I could get my battery life to about 8 hours, by tweaking background programs that run, and dimming screen/power saver mode. Is there something like this for ubuntu? Thanks for reading and for your help!

---

### Post by Paqman on 2010-07-27
I've got an EeePC 901 and a 1000HG, and TBH the function keys work out of the box on those models.

There is a package in the repos called eeepc-acpi-scripts, although it's not installed on either of my EeePCs. I suspect it's an older hack before the required fixes made it into the kernel, but it might be worth a crack.

As for battery life, there's a power management tool pre-installed, plus you could disable any services you don't need (eg: Assistive Tech). If you want to tweak further, check out [powertop](http://www.lesswatts.org/projects/powertop/).

---

### Post by I_MELT_FACES on 2010-07-27
Hey, Thanks for the fast reply. I tried installing eeepc-acpi-scripts and it gave me this: "Package dependancies cannot be resolved" I then clicked details and it gave me: eeepc-acpi-scripts
Thanks!

---

### Post by Nomadic1 on 2010-10-28
Hello everyone,  did this ever get resolved??  I just installed 10.10 netbook edition and I had the same problem with the hotkeys.  The following fixed it for me.

                     [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)
 **Ubuntu 10.4 Lucid Netbook Edition**

  Hotkeys don't work out of the box, you have to add a kernel parameter to the grub config:  
 
[LIST]
[*]     Run 'sudo gedit /etc/default/grub'
[*]Edit the line     with GRUB_CMDLINE_LINUX_DEFAULT and add " acpi_osi=Linux".     The line should then look like ->     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
[*]     Save and then run 'sudo update-grub'
[*]Reboot
[/LIST]

---

