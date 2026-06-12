---
title: "Intel Wireless 3160 very slow"
date: 2016-08-05
forum: Networking &amp; Wireless
---

### Post by efeurich on 2016-08-05
Hello all you superusers,

I'm having some trouble getting my wifi to work properly.
I have just installed Ubuntu Mate 16.04 on this laptop and found out that the wifi was very slow. I have 300up and 300 down fiber connection and on my other laptops it is lightning fast.
Also on this laptop i only see 2 bars when i&#7743; sitting in the living room (on the other laptops i have the full 5 bars in the wifi icon).

I have read some articles:
[LIST]
[*][http://z-issue.com/wp/linux-firmware-for-iwlwifi-ucode-failed-with-error-2/](http://z-issue.com/wp/linux-firmware-for-iwlwifi-ucode-failed-with-error-2/)
[*][http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)
[/LIST]

And they seem to address the problem i have. So i think i have to go the way of doing something with the kernel. As the first article explains.
But i haven't done anything yet which involves kernels :confused:
So before i mess things up i wanted to ask the community to have a look at this issue.

HARDWARE OUTPUT:
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 78
Model name:            Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz
Stepping:              3
CPU MHz:               492.070
CPU max MHz:           3100,0000
CPU min MHz:           400,0000
BogoMIPS:              5184.47
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
NUMA node0 CPU(s):     0-3

---

### Post by efeurich on 2016-08-05
I have uploaded some log files too have a look at.
Hope it helps :popcorn:

---

### Post by jeremy31 on 2016-08-06
*Thread moved to **Networking & Wireless**.*

Please see the wireless script link in my signature and post your results

And post result for ```
dpkg -l | grep linux-firmware
```

---

