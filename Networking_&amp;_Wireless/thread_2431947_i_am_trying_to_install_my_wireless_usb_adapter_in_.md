---
title: "i am trying to install my wireless usb adapter in Ubuntu"
date: 2019-11-24
forum: Networking &amp; Wireless
---

### Post by dljayasekera on 2019-11-24
I was following this thread. 

[https://ubuntuforums.org/showthread.php?t=2394372](https://ubuntuforums.org/showthread.php?t=2394372)

I am getting errors for these steps

sudo dkms add -m rtl88x2bu -v ${VER} 
Error! DKMS tree already contains: rtl88x2bu-5.2.4.4
You cannot add the same module/version combo more than once.

sudo dkms build -m rtl88x2bu -v ${VER}

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j8 KERNELRELEASE=5.0.0-36-generic KVER=5.0.0-36-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for rtl88x2bu: 5.2.4.4 not found
Error! Bad return status for module build on kernel: 5.0.0-36-generic (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log for more information.

sudo dkms install -m rtl88x2bu -v ${VER}

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j8 KERNELRELEASE=5.0.0-36-generic KVER=5.0.0-36-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for rtl88x2bu: 5.2.4.4 not found
Error! Bad return status for module build on kernel: 5.0.0-36-generic (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.2.4.4/build/make.log for more information.


sudo modprobe 88x2bu

modprobe: FATAL: Module 88x2bu not found in directory /lib/modules/5.0.0-36-generic


Any help is appreciated and I am new to Ubuntu as well.
Thanks.

---

### Post by chili555 on 2019-11-24
Let's start at the beginning and see if a fresh start helps us.

Please run and post:```
sudo dkms status
lsusb
```

---

### Post by dljayasekera on 2019-11-24
i ran again the following steps again.

sudo apt-get update
sudo apt-get install build-essential git
git clone [https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044.git](https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044.git)
cd rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044
VER=$(cat ./version)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}

[ATTACH]284475[/ATTACH]

sudo dkms add -m rtl88x2bu -v ${VER}

Error! DKMS tree already contains: rtl88x2bu-5.2.4.4
You cannot add the same module/version combo more than once.

sudo dkms status
rtl88x2bu, 5.2.4.4: added

lsusb
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

please see the attached screenshot as well. thanks.

---

### Post by chili555 on 2019-11-24
> sudo dkms status
rtl88x2bu, 5.2.4.4: [COLOR="#FF0000"]added[/COLOR]
'Added' means that it didn't build and install properly, as you know.> 
i ran again the following steps again.And it failed again. Please stop.

Let's remove the not working module: ```
sudo dkms remove rtl88x2bu/5.2.4.4 --all
```Next, let's install a newer version:```

git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.git
cd rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```

---

### Post by dljayasekera on 2019-11-25
Thank you so much and it worked. i appreciate it a lot.

---

### Post by chili555 on 2019-11-25
Awesome! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by swirl2 on 2020-03-04
Thx a lot chili555!
Just bought a new rtl88x2bu - didn't get it started.
With your help I succeeded.
swirl2

---

