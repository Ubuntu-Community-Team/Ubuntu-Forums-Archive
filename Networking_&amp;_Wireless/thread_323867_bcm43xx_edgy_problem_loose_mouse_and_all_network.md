---
title: "bcm43xx edgy problem loose mouse and all network"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by gbizeau on 2006-12-22
Hi All,

I have had Dapper Drake installed and working fine with bcm43xx firmware and fw-cutter, no problems...

Tonight I thought I would try edgy eft (6.10) so I could try beryl, looks nice, except I have one really strange problem, after I got everything installed, I proceeded to install the firmware files in /lib/firmware as usual, and I rebooted, when the system came back up, I had no mouse, and no, notta, none! network connection except lo

when I check dmesg, I don't see any loading of any network hardware. lspci shows the devices, but the kernel modules just didn't load for them.

so I remove the bcm43xx firmware files from /lib/firmware, reboot, and still have same problem....

If any one could shed some light on this, I would be gratefull... I will post any type of diagnostic info you want, I will just have to dump it to my USB Key, boot to XP and send it... Damn you Bill!!

Dell Inspirion 1300

Thanks 

Glen
](*,) ](*,) ](*,) ](*,) ](*,)

---

