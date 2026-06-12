---
title: "How do I permanently disable ACPI in Ubuntu 10.04?"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-01
I have a Toshiba A105-series laptop that is doing some quirky things (wireless and USB ports randomly failing; requires restart) that I have reason to believe may be happening due to bad ACPI support.

So I was wanting to disable this permanently, in that future kernal updates won't require me to edit a grub menu entry to keep in step.  This is for a novice Linux user who doesn't want to have to mess with any stuff like that on a regular basis.

Thanks in advanced! :)

---

### Post by davidmohammed on 2010-10-01
sounds rather drastic - some bios's have various acpi settings you can change/disable

its better to adjust your friends grub - you will not have to keep changing it when a new kernel comes along.

sudo nano /etc/default/grub

change the line

GRUB_CMDLINE_LINUX=""

to read something like

GRUB_CMDLINE_LINUX="noapic"

or
GRUB_CMDLINE_LINUX="acpi=off"

save then

sudo update-grub

to finish.

---

### Post by hhh on 2010-10-01
Use GRUB_CMDLINE_LINUX="acpi=off", noapic isn't the same thing...
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)
[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

---

### Post by davidmohammed on 2010-10-01
very true - however I do have a toshiba (although not the same model as the poster).  At first I thought it was acpi stuff.  acpi=off did fix it but at the expense of a very short battery life.  I found eventually, noapic/nolapic fixed my issues.

---

### Post by diablo75 on 2010-10-01
> **davidmohammed said:**
> 

sudo nano /etc/default/grub

Are you sure /etc/default/grub is the correct path/filename?

---

### Post by davidmohammed on 2010-10-01
definitely... if you have grub2 which is the normal for a lynx install.

If you've come from 8.04 then you may have decided to say with standard grub.  Suggest upgrade as recommended [here]("https://help.ubuntu.com/community/Grub2")

---

### Post by diablo75 on 2010-10-02
> **davidmohammed said:**
> very true - however I do have a toshiba (although not the same model as the poster).  At first I thought it was acpi stuff.  acpi=off did fix it but at the expense of a very short battery life.  I found eventually, noapic/nolapic fixed my issues.

I modified the configuration by adding the both "noapic nolapic" into the above mentioned /etc/default/grub configuration file and I am happy to report the system has not had any further glitches involving the mouse that's attached via USB or it's wireless adapter and connection to the local network.

However, the person who owns the laptop is saying their system is running "slow".  But then again, it is a Celeron processor with only 512 MB of RAM (and that's the max amount it can have on this particular laptop).

So I was wondering whether or not disabling these services might have a negative impact on system performance?

---

