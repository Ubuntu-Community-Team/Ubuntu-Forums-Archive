---
title: "Unclaimed network"
date: 2018-06-23
forum: Networking &amp; Wireless
---

### Post by baba8464 on 2018-06-23
Hi,  

My Ethernet and Wifi is not working now. I found following information. I am using ubuntu 16.04 Any help will be appreciated.

*-network UNCLAIMED    
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:f7904000-f7904fff memory:f7900000-f7903fff

  *-network UNCLAIMED
       description: Network controller
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by jeremy31 on 2018-06-23
What kernel?  Post results for ```
uname -r
```

---

### Post by baba8464 on 2018-06-23
4.4.0-119-generic

---

### Post by jeremy31 on 2018-06-23
Try ```
sudo apt-get install --reinstall linux-image-extra-4.4.0-119-generic
```
Then reboot

---

### Post by baba8464 on 2018-06-23
No, It does not work

As i said before it does't work but following message i got it.

Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 linux-image-extra-4.4.0-119-generic amd64 4.4.0-119.143
  Temporary failure resolving 'se.archive.ubuntu.com'
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 linux-image-extra-4.4.0-119-generic amd64 4.4.0-119.143
  Temporary failure resolving 'se.archive.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-4.4.0-119-generic_4.4.0-119.143_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-4.4.0-119-generic_4.4.0-119.143_amd64.deb)  Temporary failure resolving 'se.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by jeremy31 on 2018-06-23
Reboot and use the Grub menu/Advanced options to boot into an older kernel and try the command

---

### Post by baba8464 on 2018-06-23
Could you please tell me how can i boot with older kernel? I am kind of new in ubuntu.

Thanks. i did boot with older kernel. Now my both Ethernet and wifi is working.

Thanks again for help.

---

### Post by jeremy31 on 2018-06-23
Just after reboot, after the splash screen shows for the computer tap the shift key or ESC key until a menu appears.  I used to just hold my left shift key down and the Grub Menu would appear.  Then scroll down to Advanced options, press enter and scroll down to the first listing of an older kernel

You could download [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-4.4.0-119-generic_4.4.0-119.143_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-4.4.0-119-generic_4.4.0-119.143_amd64.deb) and (copy using CD/USB thumb drive)put it on the Ubuntu desktop then in terminal do
```
cd Desktop
sudo dpkg -i linux-image-extra-4.4.0-119-generic_4.4.0-119.143_amd64.deb
```
Reboot

---

### Post by baba8464 on 2018-06-23
my problem is solved, so please resolved this thread.

Thanks

---

### Post by jeremy31 on 2018-06-23
You can do that with the thread tools menu near the top right of the page, to mark as solved

---

