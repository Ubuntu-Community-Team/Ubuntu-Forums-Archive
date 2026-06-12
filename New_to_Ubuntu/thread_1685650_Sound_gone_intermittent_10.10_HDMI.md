---
title: "Sound gone intermittent 10.10 HDMI?"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by hopelessone on 2011-02-11
Hi,

Sound plays for a bit then gets cracky and goes..

```
Feb 11 14:10:28 blade kernel: [ 7094.060068] gvfsd-metadata[6219]: segfault at 8 ip 0000000000405796 sp 00007fff91cb22c0 error 4 in gvfsd-metadata[400000+d000]
Feb 11 14:15:45 blade kernel: [ 7411.048074] gvfsd-metadata[6256]: segfault at 8 ip 0000000000405796 sp 00007fffc52a81d0 error 4 in gvfsd-metadata[400000+d000]
Feb 11 14:16:45 blade kernel: [ 7471.068500] gvfsd-metadata[6293]: segfault at 8 ip 0000000000405796 sp 00007fff0f8eefc0 error 4 in gvfsd-metadata[400000+d000]
Feb 11 14:21:50 blade kernel: [ 7776.090210] gvfsd-metadata[6370]: segfault at 8 ip 0000000000405796 sp 00007ffff71f6080 error 4 in gvfsd-metadata[400000+d000]
Feb 11 14:23:28 blade kernel: [ 7874.057197] gvfsd-metadata[6501]: segfault at 8 ip 0000000000405796 sp 00007fffdf7f6be0 error 4 in gvfsd-metadata[400000+d000]
Feb 11 14:34:35 blade kernel: [ 8541.055232] gvfsd-metadata[6533]: segfault at 8 ip 0000000000405796 sp 00007fffcc0d8fe0 error 4 in gvfsd-metadata[400000+d000]
Feb 11 14:36:00 blade kernel: [ 8626.046906] gvfsd-metadata[6734]: segfault at 8 ip 0000000000405796 sp 00007fff9c7c0370 error 4 in gvfsd-metadata[400000+d000]
Feb 11 15:54:37 blade kernel: [13343.060679] gvfsd-metadata[8626]: segfault at 8 ip 0000000000405796 sp 00007fffd3996940 error 4 in gvfsd-metadata[400000+d000]
Feb 11 16:03:54 blade kernel: [13900.772293] HDA Intel 0000:00:1b.0: PCI INT A disabled
Feb 11 16:03:55 blade kernel: [13900.992806] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 11 16:03:55 blade kernel: [13901.100743] hda_codec: ALC887: BIOS auto-probing.
Feb 11 16:04:04 blade pulseaudio[3341]: ratelimit.c: 23 events suppressed
Feb 11 16:04:12 blade kernel: [13918.048671] gvfsd-metadata[9392]: segfault at 8 ip 0000000000405796 sp 00007fff159f0480 error 4 in gvfsd-metadata[400000+d000]
Feb 11 16:07:17 blade kernel: [14103.882849] HDA Intel 0000:00:1b.0: PCI INT A disabled
Feb 11 16:07:18 blade kernel: [14104.242957] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 11 16:07:18 blade kernel: [14104.358585] hda_codec: ALC887: BIOS auto-probing.
Feb 11 16:07:35 blade kernel: [14121.636285] lo: Disabled Privacy Extensions
Feb 11 16:15:14 blade kernel: [14580.792528] lo: Disabled Privacy Extensions
Feb 11 16:15:50 blade kernel: [14616.054834] gvfsd-metadata[10774]: segfault at 8 ip 0000000000405796 sp 00007fff5cac6300 error 4 in gvfsd-metadata[400000+d000]
```

can you make sense what to do so i can get sound going again?

edit: formatted new 10.10 but left the home directory

---

### Post by hopelessone on 2011-02-11
I changed TV's recently...could be the problem...?

I noticed if i pull out the HDMI1 from behind the TV and plug it into the next socket HDMI2 it goes again...

hmmm...

---

