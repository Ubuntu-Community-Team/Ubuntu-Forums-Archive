---
title: "Computer pops into and out of hibernate"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by Yerushalmi on 2010-01-28
So here's the deal. Every time I go into hibernate - whether by pressing the power button when said button is connected directly to hibernate, or by clicking hibernate in the drop-down power menu, or typing "sudo pm-hibernate" into terminal, the computer does the same rigamarole - it does a big show of powering down the terminal, writing to the drive, the screen goes black - and then instantly, back up again. Either I'll be popped right back to the terminal window I left moments earlier, or the black screen will merely be the waiting-for-the-mouse-to-move-so-it-can-present-login-screen screen saver.


Here's a look at the output of "tail -50 /var/log/pm-suspend.log":
> 
i915                  221320  3 
usb_storage            52576  2 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
atl1e                  31824  0 
video                  19380  1 i915
output                  2780  1 video
             total       used       free     shared    buffers     cached
Mem:       1018080     511036     507044          0     139388     219536
-/+ buffers/cache:     152112     865968
Swap:      5662872          0    5662872
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Thu Jan 28 20:30:40 IST 2010: performing hibernate
Thu Jan 28 20:30:59 IST 2010: Awake.
Thu Jan 28 20:30:59 IST 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: Returned exit code 1.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
As you can see, it successfully does everything to power down the computer and prepare for hibernate, activates hibernate -- and then immediately pulls the computer out of hibernate again, without my having touched a thing.

Any idea what the heck is going on?

---

### Post by nerdy_kid on 2010-01-28
ive heard that this issue is cause by not enough swap.  You can use a LiveCD and gparted to fix it.

---

### Post by Yerushalmi on 2010-01-28
I have a 5.4 gigabyte swap file....

---

### Post by warfacegod on 2010-01-28
> **Yerushalmi said:**
> I have a 5.4 gigabyte swap file....

If you have 6 GB RAM then 5.4 isn't enough. Your swap needs to be slightly bigger than your RAM.

---

### Post by Yerushalmi on 2010-01-28
I don't - I only have 994.2 MiB of memory. And 5.4GiB swap.

---

### Post by Yerushalmi on 2010-02-01
Bumping this topic. Can somebody please help me?

---

### Post by audiomick on 2010-02-01
> **Yerushalmi said:**
> I have a 5.4 gigabyte swap file....

Needs to be a swap  partition. From what I have read, Hibernate can't use a swap file.

---

### Post by Yerushalmi on 2010-02-02
I did indeed mean swap partition. Apologies; I'm new to this and not really sure what the  difference is.

---

