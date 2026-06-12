---
title: "Screen Resolution Help wanted"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by cybrax on 2009-11-02
Hi Folks,

Very impressed with Ubuntu on my Packard Bell 'Easynote' laptop works a treat, (aside from the intermittent glide pad operation, but it does that with Xp and Vista so not down to Ubuntu and probably why I got it cheap)

The only problem I do have is the screen resolution, $xrandr says the best resoultion is 800x600 and tinkering with xconf however  just upsets Ubuntu and it refuses to boot with new settings.

Vaugely recall seeing something about 'virtual' display settings as a work around for where monitor resolution is not being detected correctly could somebody point in the right direction?

---

### Post by ajgreeny on 2009-11-02
What graphics card does it have?  If you are not sure run ```
sudo lshw -C display
``` in terminal and copy the output back here.  It may be as simple as a driver update/install, so also try *System ->Administration ->Hardware Drivers* and see if there is a proprietary driver available for your card.

---

### Post by cybrax on 2009-11-02
Thanks ajgreeny, here's the information you asked for..

No proprietary drivers are in use on this system


display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0

In your hands here, its a fresh install of of 9.04 , did try auto upgrading to the latest but that crashed out so will have to wait for a disc to arrive.

---

### Post by cybrax on 2009-11-02
Finally

[http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb](http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb)

New driver installed alls well this end.

---

