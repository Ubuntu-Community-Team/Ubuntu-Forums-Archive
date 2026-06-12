---
title: "Need help regarding wifi adpater driver (88x2BU)"
date: 2019-02-21
forum: Networking &amp; Wireless
---

### Post by otto+van+chotto on 2019-02-21
Hello,

I just installed Lubuntu and I'm somewhat new to Linux and I'm not sure on how to properly install that driver. I found this driver ```
https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
``` which I'm not 100% sure works on Lubuntu.

Even if it does, I'm not sure on how to install it for instance, is DKMS pre installed on Lubuntu?

Thanks

---

### Post by wildmanne39 on 2019-02-21
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by chili555 on 2019-02-22
Let's start at the beginning. What is your exact device? Please run and post:```
lsusb
```What is your Ubuntu kernel version? Please run and post:```
uname -r
```There are two or three versions of that driver out there on the internet and not all versions compile correctly for all kernels.> Even if it does, I'm not sure on how to install it for instance, is DKMS pre installed on Lubuntu?No, it is not and neither are several other required build tools. Once we know the particulars above, we'll be in a better position to advise you step-by-step.

---

### Post by otto+van+chotto on 2019-02-22
I see, thanks!

The exact device is: ```
Bus 008 Device 003: ID 0bda:b812 Realtek Semiconductor Corp.
```

The kernel version is: ```
4.18.0-10-generic
```

---

### Post by chili555 on 2019-02-22
It looks like we're in luck! First we install dkms, the build tools and git, the mechanism by which we clone the git repository;

```
sudo apt update && sudo apt -y install dkms build-essential git
```Now we download the source code with which we'll build the driver:

```
git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.git

```From here forward, we follow the steps at the git; you may safely copy and paste each step, pressing Enter after each one:

```
cd rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```Post back if something goes wrong or we can help you in any way.

---

### Post by otto+van+chotto on 2019-02-22
Thanks for the help! It works great now.

---

### Post by chili555 on 2019-02-22
Awesome! Glad it's working. Please use Thread Tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by mpm1164 on 2019-06-29
This worked to perfection! Thank you!

> **chili555 said:**
> It looks like we're in luck! First we install dkms, the build tools and git, the mechanism by which we clone the git repository;

```
sudo apt update && sudo apt -y install dkms build-essential git
```Now we download the source code with which we'll build the driver:

```
git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.git

```From here forward, we follow the steps at the git; you may safely copy and paste each step, pressing Enter after each one:

```
cd rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```Post back if something goes wrong or we can help you in any way.

---

