---
title: "Activation of network connection failed"
date: 2020-09-28
forum: Networking &amp; Wireless
---

### Post by py-ohayo on 2020-09-28
Hello,

Since two days I have this problem on my _wired_ connection:

**Activation of network connection failed**

What have I check to fix this issue ?

Thanks.

---

### Post by py-ohayo on 2020-09-29
I've also observed strange connection that I can't delete
[IMG]https://i.postimg.cc/Kj3NmMXT/image72.png[/IMG]

---

### Post by py-ohayo on 2020-09-29
Because of this I can't connect to my external board:
[IMG]https://i.postimg.cc/XYnQMXv2/bitmap.png[/IMG]

---

### Post by py-ohayo on 2020-10-07
On the "Ask Ubuntu" forum, I found a post with a similar problem.
The proposal was to reinstall the network manager.
This didn't work in my case:

[FONT=courier new]pavel@ALABAMA:~$ sudo apt-get install --reinstall network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-decode-440 : Depends: libnvidia-compute-440 (= 440.118.02-0ubuntu1) but 440.100-0ubuntu0.18.04.1 is to be installed
 nvidia-driver-440 : Depends: libnvidia-compute-440 (= 440.118.02-0ubuntu1) but 440.100-0ubuntu0.18.04.1 is to be installed
                     Recommends: libnvidia-compute-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-decode-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-encode-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-ifr1-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-fbc1-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-gl-440:i386 (= 440.118.02-0ubuntu1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
pavel@ALABAMA:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libllvm9 libnvidia-common-455 libnvidia-extra-440 libnvidia-extra-450 linux-headers-5.4.0-45-generic linux-hwe-5.4-headers-5.4.0-45 linux-image-5.4.0-45-generic
  linux-modules-5.4.0-45-generic linux-modules-extra-5.4.0-45-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-compute-440
The following packages will be upgraded:
  libnvidia-compute-440
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
3 not fully installed or removed.
Need to get 0 B/20,9 MB of archives.
After this operation, 85,0 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 458281 files and directories currently installed.)
Preparing to unpack .../libnvidia-compute-440_440.118.02-0ubuntu1_amd64.deb ...
Unpacking libnvidia-compute-440:amd64 (440.118.02-0ubuntu1) over (440.100-0ubuntu0.18.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libnvidia-compute-440_440.118.02-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libnvidia-allocator.so', which is also in package libnvidia-extra-450:amd64 450.80.02-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-compute-440_440.118.02-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
pavel@ALABAMA:~$[/FONT]

---

### Post by exploder on 2020-10-10
I have a similar problem as well but with the WiFi connecting. Same error as you are getting. Today I just watched it fail a bunch of times, then manually connected and it worked. I tried re-installing network manager as you mentioned when I finally got online. Seems to be a problem with a recent update because everything was fine until a couple of days ago. Hopefully this will get sorted out because we are not the only ones seeing this.

---

