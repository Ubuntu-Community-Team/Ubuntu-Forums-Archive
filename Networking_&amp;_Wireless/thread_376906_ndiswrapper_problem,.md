---
title: "ndiswrapper problem,"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by kraig on 2007-03-05
I have a dell 640m laptop with the Broadcom 1390 wireless chipset.

I just installed Ubunty Edgy. The 2.6.17 kernel had problems with my keyboard (keys would be ignored, or repeated x amount of time. made using the terminal almost impossible). I had manually compiled and installed ndiswrapper 1.38 and the card worked (however, i could not get an ip through dhcp, and statically setting it would not work... but that doesn't matter)

After researching, I read the keyboard problem exists only with kernels above 2.6.15. So i downloaded 2.6.15-28, and eventually moved to 2.6.15-50 to try and solve this issue. 

PROBLEM: after compiling and installing ndiswrapper 1.38 (and 1.37) i try to modprobe it and get the following error:

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-50-amd64-generic/misc/ndiswrapper.ko): Invalid module format
```

The following is added to my dmesg:

```
[ 1307.025579] ndiswrapper: version magic '2.6.15-50-amd64-generic SMP preempt gcc-4.1' should be '2.6.15-50-amd64-generic SMP preempt gcc-4.0'
```

output from ndiswrapper -v:

```
utils version: 1.9
driver version:        1.38
vermagic:       2.6.15-50-amd64-generic SMP preempt gcc-4.1

```

uname -r: 

```
2.6.15-50-amd64-generic
```

When i changed kernels i ran the following to re-compile ndiswrapper:

```
sudo make uninstall && sudo make clean && sudo make && sudo make install
```

I've tried googling it, searching this forum. I've ran through the setup of ndiswrapper with every guide i've found and no success

Any help would be appreciated.

---

### Post by Floppyjoe on 2007-03-05
I doubt this is a solution but maybe the older kernel doesn't recognize the newer ndiswrapper versions modules. Maybe you need a slightly older version of Ndiswrapper for this to work, one that was designed for this kernel.

Just a thought.

---

### Post by kraig on 2007-03-05
I have tried ndiswrapper-1.1, 1.2, 1.37 and 1.38. All give the same version magic message

---

### Post by kraig on 2007-03-05
So I managed to find a solution. I installed gcc-4.0 (apt-get install gcc-4.0), changed my /usr/bin/gcc symlink to point to gcc-4.0.

Then i compiled the ndiswrapper with the older gcc, and it works

I'm assuming the kernel image for the 2.6.15 kernel was compiled with GCC 4.0, so the ndiswrapper compiled with 4.1 wouldn't work.

at least thats the best i could come up with.

However, i'm back to the same problem as i had before. The light comes on, I can see all networks in my area with sudo iwlist scanning, and wifi-radar, but I can't connect to any.. it seems to fail with dhcp

---

