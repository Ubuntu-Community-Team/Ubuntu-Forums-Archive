---
title: "Kernel 2.6.20.16 update breaks ndiswrapper 1.44"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by dawdler on 2007-05-28
I performed a kernel update through the ubuntu upgrade manager to 2.6.20.16.  After rebooting and loading Ubuntu (7.04) using the new kernel, my wireless card, Netgear wg311v2, is not able to connect with my WP.   I checked the loaded drivers, and ndiswrapper is loaded while acx is not loaded, which is the correct configuration 

Reverting back to the old kernel, 2.6.20.15, my wireless card works flawlessly.

Perusing the kern.log file I noticed a difference between how the new kernel and the old kernel loaded the ndiswrapper.  The new kernel recognizes the ndiswrapper to be incorrectly 1.38 while the old kernel correctly sees it as 1.44.

Kernel 2.6.20.16:
```

May 28 09:35:17 Jenny-Desktop kernel: [   43.782363] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
May 28 09:35:17 Jenny-Desktop kernel: [   43.855538] ndiswrapper: driver wg311v2 (NETGEAR, Inc.,06/17/2004,6.0.5.30) loaded
May 28 09:35:17 Jenny-Desktop kernel: [   43.855922] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 21 (level, low) -> IRQ 17
May 28 09:35:17 Jenny-Desktop kernel: [   44.444581] ndiswrapper: using IRQ 17
May 28 09:35:17 Jenny-Desktop kernel: [   44.988622] wlan0: ethernet device 00:0f:b5:07:6d:18 using NDIS driver: wg311v2, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
May 28 09:35:17 Jenny-Desktop kernel: [   44.989024] wlan0: encryption modes supported: WEP; TKIP with WPA
May 28 09:35:17 Jenny-Desktop kernel: [   44.995272] usbcore: registered new interface driver ndiswrapper

```

Kernel 2.6.20.15:
```

May 28 09:52:34 Jenny-Desktop kernel: [   42.320454] ndiswrapper version 1.44 loaded (smp=yes)
May 28 09:52:34 Jenny-Desktop kernel: [   42.390134] ndiswrapper: driver wg311v2 (NETGEAR, Inc.,06/17/2004,6.0.5.30) loaded
May 28 09:52:34 Jenny-Desktop kernel: [   42.390514] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 21 (level, low) -> IRQ 17
May 28 09:52:34 Jenny-Desktop kernel: [   42.979210] ndiswrapper: using IRQ 17
May 28 09:52:34 Jenny-Desktop kernel: [   43.222699] wlan0: ethernet device 00:0f:b5:07:6d:18 using NDIS driver: wg311v2, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
May 28 09:52:34 Jenny-Desktop kernel: [   43.222887] wlan0: encryption modes supported: WEP; TKIP with WPA
May 28 09:52:34 Jenny-Desktop kernel: [   43.229065] usbcore: registered new interface driver ndiswrapper
.
.
.
May 28 09:53:19 Jenny-Desktop kernel: [   91.472473] wlan0: no IPv6 routers present

```

Does anyone have this issue?  Will recompiling the ndiswrapper source and reinstalling it with the new kernel fix my issue?

Thanks!

---

### Post by Kobalt on 2007-05-28
I have ndiswrapper 1.44 and this new kernel installed : no problems so far... 
Kernel 2.6.20.16 refers to ndiswrapper 1.38, that's the repos version I believe. You should make sure you have nothing of ndiswrapper present when searching with Synaptic.

---

### Post by dawdler on 2007-05-29
In otherwords, I should not have ndiswrapper installed through synaptic, correct?

I believe I installed the 1.38 ndiswrapper using synaptic then installed the 1.44 version from source.  I will try out your suggestion; however, it still does not make sense why it would work with 2.6.20.15 and not with 2.6.20.16 if this was the root of the issue.

---

### Post by ollesbrorsa on 2007-05-29
If you compiled ndiswrapper from source it will only work with the kernel you had at compile time. Every time you upgrade the kernel you need to recompile.

/ollesbrorsa

---

### Post by Kobalt on 2007-05-29
Yes, you should remove any trace of ndiswrapper before compiling it. In your case, when the new kernel was installed it detected both ndiswrapper but considered the packaged only (1.38). You should try to remove this one and recompile your 1.44.

---

### Post by renerey on 2007-05-29
@dawdler

i have the same problem as you. i updated my kernel with the automatic update and my computer just hangs. i tried ctrl alt f1 to see what was the problem. so far i isolated it with ndiswrapper. i haven't tried removing ndiswrapper module with the kernel. what i noticed was when i boot with the new .16 kernel that my wifi lights just stays on unlike when it was with .15 that it blinks every 3 secs only when i connect when it stays on. so what i did was, i turned my wifi off when booting. and it seems to work just fine. i just turn it on when the loading bar went pass the middle marker when it hangs.

my wifi still works. so far i have repeated that incident and i can confirm it is the problem with mine. btw i also uses ndiswrapper-1.44. i upgraded mine from 1.43 because i thought that would fix the problem.

---

### Post by dawdler on 2007-05-30
Ok.  I know what happened.  Since I had installed the synaptic version of ndiswrapper v 1.38 before doing the kernel update, when I actually did the kernel update, the 1.38 ndiswrapper driver module was dropped into the "/lib/modules/2.6.20-16-generic/..." directory by synaptic b/c synaptic had no idea of the 1.44 ndiswrapper.  This explains my kern.log output!

Redoing a "make install" of the 1.44 ndiswrapper source while using the 2.6.20-16 kernel solved the issue (thanks ollesbrorsa).  However, to avoid confusion, removing the synaptic ndiswrapper as Kobalt recommends is a good suggestion which I did.  Thanks fellas :KS.

renerey,
Check your kern.log to see where the boot up process hangs when your wireless is on in order to confirm that it is the ndiswrapper.  If it is, try booting with wireless off and recompiling and reinstalling the 1.44 source.

My issue was not a freeze @ boot up, but rather lack of wireless functionality after login.

---

### Post by ollesbrorsa on 2007-05-30
> **dawdler said:**
> 
Redoing a "make install" of the 1.44 ndiswrapper source while using the 2.6.20-16 kernel solved the issue (thanks ollesbrorsa).  However, to avoid confusion, removing the synaptic ndiswrapper as Kobalt recommends is a good suggestion which I did.  Thanks fellas :KS.


Excellent, glad I could help out. 
To further help the community a [SOLVED] tag on this thread woul be nice. I'm not sure if the OP can do this or if we need moderator intervention.

Br,
/ollesbrorsa

---

