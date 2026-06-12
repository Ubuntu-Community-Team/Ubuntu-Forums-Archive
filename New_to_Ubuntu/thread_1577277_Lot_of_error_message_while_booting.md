---
title: "Lot of error message while booting"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by dagarshali on 2010-09-18
HI,
I have ubuntu 64 bit lucid installed. When I boot up, I get a lot of error messages. Here, I am posting the output of dmesg |grep error. Could anybody please let me what these errors are and how to fix them.
> [   10.214856] end_request: I/O error, dev sr0, sector 0
[   10.215026] Buffer I/O error on device sr0, logical block 0
[   10.215194] Buffer I/O error on device sr0, logical block 1
[   10.216435] end_request: I/O error, dev sr0, sector 0
[   10.216602] Buffer I/O error on device sr0, logical block 0
[   10.216769] Buffer I/O error on device sr0, logical block 1
[   10.218012] end_request: I/O error, dev sr0, sector 0
[   10.218196] Buffer I/O error on device sr0, logical block 0
[   10.218370] Buffer I/O error on device sr0, logical block 1
[   10.222828] end_request: I/O error, dev sr0, sector 0
[   10.223019] Buffer I/O error on device sr0, logical block 0
[   10.223193] Buffer I/O error on device sr0, logical block 1
[   10.224431] end_request: I/O error, dev sr0, sector 0
[   10.224599] Buffer I/O error on device sr0, logical block 0
[   10.224767] Buffer I/O error on device sr0, logical block 1
[   10.225999] end_request: I/O error, dev sr0, sector 0
[   10.227497] end_request: I/O error, dev sr0, sector 0
[   10.228693] end_request: I/O error, dev sr0, sector 0
[   10.230163] end_request: I/O error, dev sr0, sector 0
[   10.231551] end_request: I/O error, dev sr0, sector 0
[   10.233129] end_request: I/O error, dev sr0, sector 56
[   10.234377] end_request: I/O error, dev sr0, sector 0
[   10.235836] end_request: I/O error, dev sr0, sector 0
[   10.237009] end_request: I/O error, dev sr0, sector 0
[   10.238411] end_request: I/O error, dev sr0, sector 0
[   10.239584] end_request: I/O error, dev sr0, sector 0
[   10.241267] end_request: I/O error, dev sr0, sector 0
[   10.242595] end_request: I/O error, dev sr0, sector 0
[   10.244124] end_request: I/O error, dev sr0, sector 0
[   10.245297] end_request: I/O error, dev sr0, sector 0
[   10.246716] end_request: I/O error, dev sr0, sector 0
[   10.247906] end_request: I/O error, dev sr0, sector 0
[   10.249329] end_request: I/O error, dev sr0, sector 0
[   10.250610] end_request: I/O error, dev sr0, sector 0
[   10.252135] end_request: I/O error, dev sr0, sector 0
[   10.253385] end_request: I/O error, dev sr0, sector 0
[   10.255038] end_request: I/O error, dev sr0, sector 0
[   10.256376] end_request: I/O error, dev sr0, sector 8
[   10.257844] end_request: I/O error, dev sr0, sector 8
[   10.259066] end_request: I/O error, dev sr0, sector 8
[   10.260655] end_request: I/O error, dev sr0, sector 8
[   10.261851] end_request: I/O error, dev sr0, sector 24
[   10.263310] end_request: I/O error, dev sr0, sector 24
[   10.264634] end_request: I/O error, dev sr0, sector 24
[   10.266163] end_request: I/O error, dev sr0, sector 24
[   10.267481] end_request: I/O error, dev sr0, sector 56
[   10.268955] end_request: I/O error, dev sr0, sector 56
[   10.270172] end_request: I/O error, dev sr0, sector 56
[   10.271764] end_request: I/O error, dev sr0, sector 56
[   10.272959] end_request: I/O error, dev sr0, sector 120
[   10.274418] end_request: I/O error, dev sr0, sector 120
[   10.275666] end_request: I/O error, dev sr0, sector 120
[   10.277155] end_request: I/O error, dev sr0, sector 120
[   10.278405] end_request: I/O error, dev sr0, sector 0
[   10.280012] end_request: I/O error, dev sr0, sector 0
[   10.281277] end_request: I/O error, dev sr0, sector 8
[   10.282679] end_request: I/O error, dev sr0, sector 8
[   10.283867] end_request: I/O error, dev sr0, sector 24
[   10.285293] end_request: I/O error, dev sr0, sector 24
[   10.286482] end_request: I/O error, dev sr0, sector 56
[   10.287941] end_request: I/O error, dev sr0, sector 56
[   10.289263] end_request: I/O error, dev sr0, sector 120
[   10.290872] end_request: I/O error, dev sr0, sector 120
[   10.292119] end_request: I/O error, dev sr0, sector 0
[   10.293579] end_request: I/O error, dev sr0, sector 0
[   10.294756] end_request: I/O error, dev sr0, sector 0
[   10.296213] end_request: I/O error, dev sr0, sector 0
[   10.297390] end_request: I/O error, dev sr0, sector 0
[   10.298984] end_request: I/O error, dev sr0, sector 0
[   10.300242] end_request: I/O error, dev sr0, sector 16
[   10.301839] end_request: I/O error, dev sr0, sector 128
[   10.303157] end_request: I/O error, dev sr0, sector 128
[   10.304616] end_request: I/O error, dev sr0, sector 128
[   10.305833] end_request: I/O error, dev sr0, sector 16
[   10.307332] end_request: I/O error, dev sr0, sector 128
[   10.308511] end_request: I/O error, dev sr0, sector 64
[   10.310048] end_request: I/O error, dev sr0, sector 64
[   10.311453] end_request: I/O error, dev sr0, sector 64
[   10.313005] end_request: I/O error, dev sr0, sector 64
[   10.314323] end_request: I/O error, dev sr0, sector 64
[   10.315791] end_request: I/O error, dev sr0, sector 64
[   10.317008] end_request: I/O error, dev sr0, sector 64
[   10.318514] end_request: I/O error, dev sr0, sector 64
[   10.319716] end_request: I/O error, dev sr0, sector 64
[   10.321261] end_request: I/O error, dev sr0, sector 64
[   10.322511] end_request: I/O error, dev sr0, sector 256
[   10.323993] end_request: I/O error, dev sr0, sector 256
[   10.325242] end_request: I/O error, dev sr0, sector 264
[   10.326840] end_request: I/O error, dev sr0, sector 264
[   10.328021] end_request: I/O error, dev sr0, sector 272
[   10.329409] end_request: I/O error, dev sr0, sector 272
[   10.330687] end_request: I/O error, dev sr0, sector 768
[   10.332110] end_request: I/O error, dev sr0, sector 768
[   10.333302] end_request: I/O error, dev sr0, sector 776
[   10.334761] end_request: I/O error, dev sr0, sector 776
[   10.336083] end_request: I/O error, dev sr0, sector 784
[   10.337618] end_request: I/O error, dev sr0, sector 784
[   10.338939] end_request: I/O error, dev sr0, sector 0
[   10.340501] end_request: I/O error, dev sr0, sector 0
[   10.341719] end_request: I/O error, dev sr0, sector 0
[   10.343224] end_request: I/O error, dev sr0, sector 0
[   10.344419] end_request: I/O error, dev sr0, sector 0
[   10.345878] end_request: I/O error, dev sr0, sector 16
[   10.347125] end_request: I/O error, dev sr0, sector 0
[   10.348607] end_request: I/O error, dev sr0, sector 0
[   10.349855] end_request: I/O error, dev sr0, sector 0
[   10.351542] end_request: I/O error, dev sr0, sector 0
[   10.352720] end_request: I/O error, dev sr0, sector 0
[   10.354111] end_request: I/O error, dev sr0, sector 0
[   10.355303] end_request: I/O error, dev sr0, sector 0
[   10.356832] end_request: I/O error, dev sr0, sector 0
[   10.358169] end_request: I/O error, dev sr0, sector 0
[   10.359735] end_request: I/O error, dev sr0, sector 0
[   10.361140] end_request: I/O error, dev sr0, sector 0
[   10.362599] end_request: I/O error, dev sr0, sector 0
[   10.363816] end_request: I/O error, dev sr0, sector 128
[   10.365317] end_request: I/O error, dev sr0, sector 128
[   10.366512] end_request: I/O error, dev sr0, sector 16
[   10.367978] end_request: I/O error, dev sr0, sector 0
[   10.369225] end_request: I/O error, dev sr0, sector 0
[   10.371043] end_request: I/O error, dev sr0, sector 8
[   10.372289] end_request: I/O error, dev sr0, sector 16
[   10.373770] end_request: I/O error, dev sr0, sector 0
[   10.374987] end_request: I/O error, dev sr0, sector 0
[   10.376488] end_request: I/O error, dev sr0, sector 0
[   10.377685] end_request: I/O error, dev sr0, sector 0
[   10.379212] end_request: I/O error, dev sr0, sector 0
[   10.380633] end_request: I/O error, dev sr0, sector 0
[   10.382210] end_request: I/O error, dev sr0, sector 8
[   10.383526] end_request: I/O error, dev sr0, sector 128
[   10.384985] end_request: I/O error, dev sr0, sector 0
[   10.386203] end_request: I/O error, dev sr0, sector 0
[   10.387704] end_request: I/O error, dev sr0, sector 4096
[   10.398896] end_request: I/O error, dev sr0, sector 0
[   10.400075] end_request: I/O error, dev sr0, sector 0
[   10.401554] end_request: I/O error, dev sr0, sector 0
[   44.171116] ata2.00: irq_stat 0x08000000, interface fatal error
[   44.171137]          res 50/00:03:00:04:00/00:00:00:00:00/a0 Emask 0x12 (ATA bus error)

Regards,
Vishwa

---

### Post by davidmohammed on 2010-09-18
possibly [this]("http://ubuntuforums.org/showthread.php?t=1015569") could be your issue?

---

### Post by Rubi1200 on 2010-09-18
> dev sr0
Isn't that the CD-drive?

Something in there perhaps you forgot to take out?

---

