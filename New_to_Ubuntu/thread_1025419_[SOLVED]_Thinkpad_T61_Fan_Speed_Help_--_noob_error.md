---
title: "[SOLVED] Thinkpad T61 Fan Speed Help -- noob error"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by d.asahi on 2008-12-30
I just put Ubuntu 8.04 on my Lenovo Thinkpad T61 and the fans aren't blowing at nearly the rate they should be, sometimes not at all -- even when the CPU shows intense activity. I see by other threads that [others have had the same issue]("http://ubuntuforums.org/showthread.php?t=872108&highlight=t61+fan+speed"). 

Unfortunately, being pretty much a noob, I have a limited idea of what all their instructions mean. I feel like I got close, but I'm missing some really simple step that I just haven't learned yet.

I downloaded [the recommended program for controlling fan speed]("http://linux.die.net/man/8/fancontrol"), but there's a step that's got to be done first in the terminal that's stopping me.

The instruction from the readme says this:
```
You are required to have the Linux kernel with 'thinkpad-acpi' patch.
You must also enable manual control for your fans. For Linux 2.6.22 and above,
you must add 'fan_control=1' as a module parameter to 'thinkpad-acpi'.
For example, in Debian Lenny (and Ubuntu 8.04), you must add the following
to "/etc/modprobe.d/options":
        options thinkpad_acpi fan_control=1
 
Having done so, reboot. Now you'll be able to use this program easily.
```

And this is what I did:
```
da@Lapper-T61:~$ cd /
da@Lapper-T61:/$ cd etc
da@Lapper-T61:/etc$ cd modprobe.d
da@Lapper-T61:/etc/modprobe.d$ ls
aliases       blacklist-framebuffer  isapnp             options
alsa-base     blacklist-modem        libpisock9         toshiba_acpi.modprobe
arch          blacklist-oss          libsane
arch-aliases  blacklist-watchdog     lrm-video
blacklist     fuse                   nvidia-kernel-nkc
da@Lapper-T61:/etc/modprobe.d$ options thinkpad_acpi fan_speed=1
bash: options: command not found
da@Lapper-T61:/etc/modprobe.d$ sudo options thinkpad_acpi fan_speed=1
sudo: options: command not found
```

I also tried it using "sudo su", which also did not work.

Many, many thanks to the person who can set me straight on what I'm doing wrong.

And bonus points if you can tell me how to set this program to run at startup so I don't have to run it manually every time I start my computer.


*The details, if you need them: Lenovo T61 running 8.04.1 x86 on an Intel Centrino dual-core processor, nvidia nvs 140m graphics card.*

---

### Post by Partyboi2 on 2008-12-30
```
gksu gedit /etc/modprobe.d/options
``` then add
```
options thinkpad_acpi fan_control=1
``` then save and reboot.

---

### Post by d.asahi on 2008-12-30
Ah, thank you very much. I know it was something simple that I just didn't know about yet. :D

Solved.

---

