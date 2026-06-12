---
title: "AC600 wireless issues"
date: 2018-03-02
forum: Networking &amp; Wireless
---

### Post by Penguin360 on 2018-03-02
I have the same issue. My USB 5G wifi adapter has been working until I upgraded the kernel to 4.13.0.36. Now my Ubuntu 17.10 does not recognize the adapter. I used to install rtl8812au-dkms package in Ubuntu repository and it worked, but now it does not. I guess rtl8812au-dkms package has not been updated to the latest kernel build? 

Also, there are several rtl8812au drivers on github, which one is the best one to go with?

Thanks,

---

### Post by chili555 on 2018-03-02
> **Penguin360 said:**
> I have the same issue. My USB 5G wifi adapter has been working until I upgraded the kernel to 4.13.0.36. Now my Ubuntu 17.10 does not recognize the adapter. I used to install rtl8812au-dkms package in Ubuntu repository and it worked, but now it does not. I guess rtl8812au-dkms package has not been updated to the latest kernel build? 

Also, there are several rtl8812au drivers on github, which one is the best one to go with?

Thanks,I would purge it:```
sudo apt purge rtl8812au-dkms 
```Then follow the process above to install the 4.2.2 version. It builds and installs fine on my 4.13.0-36 kernel. I haven't the device so I can't tell if it works well or not. I just know that the driver builds and installs.

If that doesn't get you going, please start a new thread.

---

### Post by jeremy31 on 2018-03-02
Split from [https://ubuntuforums.org/showthread.php?t=2386168](https://ubuntuforums.org/showthread.php?t=2386168) Penguin360, please do not highjack someone else's thread.
I would like to see results for ```
modinfo 8812au
```
Before following chili555's instructions

---

### Post by Penguin360 on 2018-03-02
> **jeremy31 said:**
> Split from [https://ubuntuforums.org/showthread.php?t=2386168](https://ubuntuforums.org/showthread.php?t=2386168) Penguin360, please do not highjack someone else's thread.
I would like to see results for ```
modinfo 8812au
```
Before following chili555's instructions

Sorry I didn't mean to hijack his post. Since I have the same issue with the OP, I thought I could ask some questions.

I will be careful next time.

---

### Post by jeremy31 on 2018-03-03
There are a couple possible reasons your module did not work in the new kernel.
The rtl8812au-dkms package has an issue with the dkms.conf file and it will build for the old kernel rather than the new one.  You can edit the /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf and change it so that it is
```
PACKAGE_NAME="rtl8812au"
PACKAGE_VERSION="4.3.8.12175.20140902+dfsg"
BUILT_MODULE_NAME[0]="8812au"
MAKE[0]="'make' all KVER=${kernelver}"
CLEAN="'make' clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"
```

The installed version only has MAKE[0]="'make' all and that causes the issue.  You can make the change and then
```
sudo dkms remove rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
sudo dkms install rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
```

---

