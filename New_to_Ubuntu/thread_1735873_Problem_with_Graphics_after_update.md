---
title: "Problem with Graphics after update"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by poppi3579 on 2011-04-21
My desktop is oversize after updating to the most current software.  I tried everything.  I have searched the forum and nothing is working for me.  Please help.  I went into System-Preference-Monitors and I get this error.

**You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.**  

I do not know what to do from here.  If someone could help that would be great.

---

### Post by rosencrantz on 2011-04-21
I hope I understood correctly what you posted - 
I gather that after a system update your screen resolution is too large (the desktop doesn't fit the screen) and you tried fixing it with the nvidia settngs utility? And there the system complained about missing the nvidia driver?
First, we need some information about the card and what driver you are currently running. Please post the output of 
[FONT="Courier New"]sudo lshw -C video[/FONT]
and of [FONT="Courier New"]xrandr[/FONT].
What's your screen's native resolution?

---

### Post by yetiman64 on 2011-04-21
> **poppi3579 said:**
> **...(just run `nvidia-xconfig` as root)...**.

Open a terminal and input
```
sudo nvidia-xconfig
```
do a restart of the machine.

---

### Post by poppi3579 on 2011-04-22
> **yetiman64 said:**
> Open a terminal and input
```
sudo nvidia-xconfig
```do a restart of the machine.


I tried the command " sudo nvidia-xconfig"  I got command not found.  I then tried the command without sudo in front and i got Error: Unable to write to directory'/etc/x11

---

### Post by poppi3579 on 2011-04-22
> **rosencrantz said:**
> I hope I understood correctly what you posted - 
I gather that after a system update your screen resolution is too large (the desktop doesn't fit the screen) and you tried fixing it with the nvidia settngs utility? And there the system complained about missing the nvidia driver?
First, we need some information about the card and what driver you are currently running. Please post the output of 
[FONT=Courier New]sudo lshw -C video[/FONT]
and of [FONT=Courier New]xrandr[/FONT].
What's your screen's native resolution?

Below is what pulled up after the command.


*-display               
       description: VGA compatible controller
       product: G86 [GeForce 8500 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:dc000000-ddffffff ioport:dc80(size=128) memory:dfe00000-dfe1ffff(prefetchable)






I hope this is what you needed.

---

### Post by poppi3579 on 2011-04-22
Its fix.   Thanks

---

