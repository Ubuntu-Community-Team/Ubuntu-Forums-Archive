---
title: "Intel Wifi device not working on my Dell Latitude 5530 from Ubuntu 22.04.2 on"
date: 2023-05-08
forum: Networking &amp; Wireless
---

### Post by davyhermans on 2023-05-08
Hello all,

Since I updated my PC Dell Latitude 5530 from Ubuntu 22.04.1 to Ubuntu 22.04.2,
my internal Intel Wifi device doesn't work any more.
This is what is returned by dmesg:

```
[ 1250.974255] Intel(R) Wireless WiFi driver for Linux
[ 1251.366492] iwlwifi 0000:00:14.3: CSR_RESET = 0x11
[ 1251.366497] iwlwifi 0000:00:14.3: Host monitor block 0x0 vector 0x0
[ 1251.366648] iwlwifi 0000:00:14.3: value [iter 0]: 0x00000000
[ 1251.366805] iwlwifi 0000:00:14.3: value [iter 1]: 0x00000000
[ 1251.366960] iwlwifi 0000:00:14.3: value [iter 2]: 0x00000000
[ 1251.367117] iwlwifi 0000:00:14.3: value [iter 3]: 0x00000000
[ 1251.367274] iwlwifi 0000:00:14.3: value [iter 4]: 0x00000000
[ 1251.367432] iwlwifi 0000:00:14.3: value [iter 5]: 0x00000000
[ 1251.367590] iwlwifi 0000:00:14.3: value [iter 6]: 0x00000000
[ 1251.367747] iwlwifi 0000:00:14.3: value [iter 7]: 0x00000000
[ 1251.367903] iwlwifi 0000:00:14.3: value [iter 8]: 0x00000000
[ 1251.368060] iwlwifi 0000:00:14.3: value [iter 9]: 0x00000000
[ 1251.368218] iwlwifi 0000:00:14.3: value [iter 10]: 0x00000000
[ 1251.368376] iwlwifi 0000:00:14.3: value [iter 11]: 0x00000000
[ 1251.368533] iwlwifi 0000:00:14.3: value [iter 12]: 0x00000000
[ 1251.368691] iwlwifi 0000:00:14.3: value [iter 13]: 0x00000000
[ 1251.368849] iwlwifi 0000:00:14.3: value [iter 14]: 0x00000000
[ 1251.368849] iwlwifi 0000:00:14.3: Host monitor block 0x0 vector 0x1
[ 1251.369007] iwlwifi 0000:00:14.3: value [iter 0]: 0x00000000
[ 1251.369164] iwlwifi 0000:00:14.3: value [iter 1]: 0x00000000
[ 1251.369322] iwlwifi 0000:00:14.3: value [iter 2]: 0x00000000
[ 1251.369479] iwlwifi 0000:00:14.3: value [iter 3]: 0x00000000
[ 1251.369637] iwlwifi 0000:00:14.3: value [iter 4]: 0x00000000
[ 1251.369794] iwlwifi 0000:00:14.3: value [iter 5]: 0x00000000
[ 1251.369950] iwlwifi 0000:00:14.3: value [iter 6]: 0x00000000
[ 1251.370106] iwlwifi 0000:00:14.3: value [iter 7]: 0x00000000
[ 1251.370264] iwlwifi 0000:00:14.3: value [iter 8]: 0x00000000
[ 1251.370419] iwlwifi 0000:00:14.3: value [iter 9]: 0x00000000
[ 1251.370577] iwlwifi 0000:00:14.3: value [iter 10]: 0x00000000
[ 1251.370732] iwlwifi 0000:00:14.3: value [iter 11]: 0x00000000
[ 1251.370890] iwlwifi 0000:00:14.3: value [iter 12]: 0x00000000
[ 1251.371047] iwlwifi 0000:00:14.3: value [iter 13]: 0x00000000
[ 1251.371205] iwlwifi 0000:00:14.3: value [iter 14]: 0x00000000
[ 1251.371206] iwlwifi 0000:00:14.3: Host monitor block 0x0 vector 0x6
[ 1251.371363] iwlwifi 0000:00:14.3: value [iter 0]: 0x00000000
[ 1251.371520] iwlwifi 0000:00:14.3: value [iter 1]: 0x00000000
[ 1251.371678] iwlwifi 0000:00:14.3: value [iter 2]: 0x00000000
[ 1251.371836] iwlwifi 0000:00:14.3: value [iter 3]: 0x00000000
[ 1251.371991] iwlwifi 0000:00:14.3: value [iter 4]: 0x00000000
[ 1251.372148] iwlwifi 0000:00:14.3: value [iter 5]: 0x00000000
[ 1251.372304] iwlwifi 0000:00:14.3: value [iter 6]: 0x00000000
[ 1251.372460] iwlwifi 0000:00:14.3: value [iter 7]: 0x00000000
[ 1251.372617] iwlwifi 0000:00:14.3: value [iter 8]: 0x00000000
[ 1251.372775] iwlwifi 0000:00:14.3: value [iter 9]: 0x00000000
[ 1251.372933] iwlwifi 0000:00:14.3: value [iter 10]: 0x00000000
[ 1251.373089] iwlwifi 0000:00:14.3: value [iter 11]: 0x00000000
[ 1251.373246] iwlwifi 0000:00:14.3: value [iter 12]: 0x00000000
[ 1251.373404] iwlwifi 0000:00:14.3: value [iter 13]: 0x00000000
[ 1251.373560] iwlwifi 0000:00:14.3: value [iter 14]: 0x00000000
[ 1251.373560] iwlwifi 0000:00:14.3: Host monitor block 0x22 vector 0x0
[ 1251.373718] iwlwifi 0000:00:14.3: value [iter 0]: 0x00000000
[ 1251.373735] iwlwifi: probe of 0000:00:14.3 failed with error -110

```
Also, when I use "Try Ubuntu" with the USB stick containing Ubuntu 22.04.2 it doesn't work.
But it works when I use "Try Ubuntu" with the USB stick containing Ubuntu 22.04.1.

Any idea, what has been changed and what can be the solution?

Tx in advance!

Davy Hermans

---

### Post by slickymaster on 2023-05-08
Thread moved to **Networking & Wireless** for a better fit

---

### Post by davyhermans on 2023-05-12
See
[https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2017790](https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2017790)

[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][Jeremy (wa113y3s)]("https://launchpad.net/~wa113y3s") wrote on 2023-04-30:[/TD]
[TD][/TD]
[TD][/TD]
[TD="class: bug-comment-index"][#14]("https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2017790/comments/14")[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]David, power off the laptop and remove battery and power cord, then press and hold power button for 30 seconds, install battery and power cord, then boot. If the battery isn't easy to access, just remove power cord and hold power button for 30 seconds
[/FONT]

[/FONT][/COLOR]
This worked for my colleague and me!

---

### Post by garyembler on 2023-05-23
> **davyhermans said:**
> See
[https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2017790](https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2017790)

[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][Jeremy (wa113y3s)]("https://launchpad.net/~wa113y3s") wrote on 2023-04-30:[/TD]
[TD][/TD]
[TD][/TD]
[TD="class: bug-comment-index"][#14]("https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2017790/comments/14")[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]David, power off the laptop and remove battery and power cord, then press and hold power button for 30 seconds, install battery and power cord, then boot. If the battery isn't easy to access, just remove power cord and hold power button for 30 seconds
[/FONT]

[/FONT][/COLOR]
This worked for my colleague and me!


This did not work for me on a Dell Latitude E7240 notebook. Here is dmesg output in case this helps:

[    3.069965] Intel(R) Wireless WiFi driver for Linux
[    3.109284] iwlwifi 0000:02:00.0: loaded firmware version 17.3216344376.0 7260-17.ucode op_mode iwlmvm
[    3.172180] Console: switching to colour dummy device 80x25
[    3.172238] i915 0000:00:02.0: vgaarb: deactivate vga console
[    3.181181] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.4)
[    3.194091] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.207074] wl: loading out-of-tree module taints kernel.
[    3.207081] wl: module license 'MIXED/Proprietary' taints kernel.
[    3.207083] Disabling lock debugging due to kernel taint
[    3.226743] mc: Linux media interface: v0.10
[    3.227856] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    3.234272] iwlwifi 0000:02:00.0: reporting RF_KILL (radio disabled)
[    3.234294] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[    3.235503] wl: module verification failed: signature and/or required key missing - tainting kernel

Thanks,

Gary

---

### Post by chili555 on 2023-05-23
>  iwlwifi 0000:02:00.0: reporting RF_KILL ([COLOR="#FF0000"]radio disabled[/COLOR])Please find the Airplane Mode switch on the left side and switch it.

---

### Post by garyembler on 2023-05-24
Thanks for your suggestion. On close examination, the switch was partially in the off position, enough to turn off the radios. Moving the switch to the fully-on position restored the WiFi. This notebook is new to me and I probably moved the switch without realizing it by handling the notebook.

---

### Post by chili555 on 2023-05-24
> **garyembler said:**
> Thanks for your suggestion. On close examination, the switch was partially in the off position, enough to turn off the radios. Moving the switch to the fully-on position restored the WiFi. This notebook is new to me and I probably moved the switch without realizing it by handling the notebook.Everyone has done it; I did myself yesterday!

Glad it's working! Please use thread tools at the top to mark Solved.

---

### Post by garyembler on 2023-05-24
I don't see a "mark Solved" selection in the Thread Tools. Maybe since I just joined I don't yet have this privilege, or thread starter Davy must do this.

I chimed-in because my issue was similar on a similar notebook. The WiFi literally stopped working right after an update (over WiFi). This is when the switch must have moved. Talk about a coincidence...

---

