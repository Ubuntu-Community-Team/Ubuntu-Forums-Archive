---
title: "Sound Drivers"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Rabz on 2009-07-12
im using onboard sound (no physical sound card) in my machine.
 
How can i check if it has the right drivers or view details of some sort??

---

### Post by nhasian on 2009-07-12
in a terminal type

```
lshw -C multimedia
```

it will say driver= and module= that tells which driver its using.  if it says UNCLAIMED then no driver is loaded.

---

### Post by ~sHyLoCk~ on 2009-07-12
> **Rabz said:**
> im using onboard sound (no physical sound card) in my machine.
 
How can i check if it has the right drivers or view details of some sort??

```
lspci -v | grep snd
```

---

### Post by Rabz on 2009-07-12
[EMAIL="rabz@A3:~$"]rabz@A3:~$[/EMAIL] lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: [EMAIL="pci@0000:04:01.0"]pci@0000:04:01.0[/EMAIL]
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
[EMAIL="rabz@A3:~$"]rabz@A3:~$[/EMAIL]

---

### Post by Rabz on 2009-07-12
[EMAIL="rabz@A3:~$"]rabz@A3:~$[/EMAIL] lspci -v | grep snd
Kernel modules: snd-hda-intel
[EMAIL="rabz@A3:~$"]rabz@A3:~$[/EMAIL]

---

### Post by Rabz on 2009-07-12
OMG!! WHAHAHAAH!!
 
sound was on mute :lolflag:
 
thanx for the help guys!

---

