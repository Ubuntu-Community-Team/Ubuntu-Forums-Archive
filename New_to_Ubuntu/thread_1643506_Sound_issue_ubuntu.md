---
title: "Sound issue ubuntu"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-12
Right now i am running 10.10 and about once every 10 times ubuntu starts the sound doesnt work.  The fix for it is to restart the computer, but i would like to fix the issue. Is their any possible suggestions?  Is their a way to restart the sound driver? Thanks

---

### Post by karthick87 on 2010-12-12
Check out these links,

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Sef on 2010-12-12
1) So what you want to do when the sound does not start is have a way to restart the sound driver without rebooting Ubuntu, until a fix is found?

2) What sound card do you have?

---

### Post by hunter99507 on 2010-12-12
> **Sef said:**
> 1) So what you want to do when the sound does not start is have a way to restart the sound driver without rebooting Ubuntu, until a fix is found?

2) What sound card do you have?

Basically I am not sure what is causing the issue, a guess would be that the driver is not loading proporly.  Now I dont know if could cause it, but I have the theme macbuntu installed.

As far as a sound card I am not sure what it is exactly. I think it is a realtek but not sure.  Is there a way to check it?

---

### Post by karthick87 on 2010-12-12
Post the output,
```
sudo lshw -C sound
```

---

### Post by hunter99507 on 2010-12-12
*-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:f0400000-f0403fff

---

