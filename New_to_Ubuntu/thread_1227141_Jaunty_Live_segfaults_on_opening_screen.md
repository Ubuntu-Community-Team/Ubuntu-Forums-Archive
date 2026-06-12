---
title: "Jaunty Live segfaults on opening screen"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by tedw on 2009-07-30
PC is Dell GX260 which runs Hardy without problems.

ubuntu 9.04 live (Jaunty) gives the message "nautilus closed unexpectedly".

sudo dmesg:tail gave

[   77.879486] lp0: using parport0 (interrupt-driven).
[   78.572863] [drm] Initialized drm 1.1.0 20060810
[   78.857144] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   78.857157] pci 0000:00:02.0: setting latency timer to 64
[   78.857471] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   78.938400] [drm:i915_setparam] *ERROR* unknown parameter 4
[   78.938448] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   80.002833] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   80.185509] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  107.592461] nautilus[4534]: segfault at 986b000 ip b630a7dd sp b62f8fc0 error 4 in libbrasero-media.so.0.1.1[b62fa000+1e000]

Any clues folks ?   

Or is Jaunty just another version I cannot use ?

tedw

---

### Post by nhasian on 2009-07-30
just out of curiosity, can you give Karmic Alpha3 LiveCD a spin?

[http://cdimage.ubuntu.com/releases/karmic/alpha-3/](http://cdimage.ubuntu.com/releases/karmic/alpha-3/)

---

### Post by tedw on 2009-07-31
Hi Nhasian,

Problems with karmic alpha-3 at this time are worse ! 

A brief flash on the screen to the effect "loading, please wait" 
and nothing more is seen.  After a while the characteristic tick-tock sound is heard but on the screen, still nothing. 

Same effect on trying to verify the CD. (without the sound, of course.)

tedw

---

### Post by nothingspecial on 2009-07-31
It`s an unresolved bug with brassero. Try removing it along with libbrasero-media0 and see if that helps. You can use nautilus cd burner instead.

---

