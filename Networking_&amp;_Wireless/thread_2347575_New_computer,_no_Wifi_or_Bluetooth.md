---
title: "New computer, no Wifi or Bluetooth"
date: 2016-12-26
forum: Networking &amp; Wireless
---

### Post by xelaot on 2016-12-26
I just got a new computer and I have installed Ubuntu 16.04, but I have no access to Wifi and cannot use bluetooth to make a tethered connection to my phone, I have tried to install ndiswrapper to use the windows drivers, but I feel that I have either not installed one of the dependencies correctly or something else. Thanks!

EDIT: I have a HP Spectre x360 (late 2016 model) and an Intel Dual Band Wireless-AC 8265 network card (PCI) .

---

### Post by wildmanne39 on 2016-12-26
Please post the answer here so everyone that may have the same issue can benefit from the solution.
Thanks

---

### Post by xelaot on 2016-12-27
Because my computer was made after Ubuntu 16.04, 16.04 had problems using my Wifi and bluetooth. The solution was to install 16.10.

---

### Post by hyburn on 2016-12-27
please open a terminal (ctrl+alt+t) and type:

lspci if your wireless is pci device

or

lsusb if you are using a usb wireless device

then post the results here please

---

### Post by slickymaster on 2016-12-27
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2016-12-27
> **xelaot said:**
> Because my computer was made after Ubuntu 16.04, 16.04 had problems using my Wifi and bluetooth. The solution was to install 16.10.Exactly!

The Intel 8265 device is covered in 16.10 but, because it is so new, not 16.04.

Forget ndiswrapper; in this case, it will never work.

---

### Post by linlinz on 2016-12-28
I installed 16.04 on the same model but no sound and wifi. After updating the kernel to 4.8-generic, sound and wifi works but still no bluetooth. 

It is said the Intel 8265 is supported by kernel 4.8. Do I have to upgrade to Ubuntu 16.10 to make bluetooth work? Thanks

---

### Post by jeremy31 on 2016-12-28
Since you have the 4.8 kernel installed you may just need the updated linux-firmware package
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/
sudo dpkg -i linux-firmware_1.161.1_all.deb
```

Reboot

---

### Post by chili555 on 2016-12-28
I think Jeremy means:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux*.deb
```

---

### Post by jeremy31 on 2016-12-28
> **chili555 said:**
> I think Jeremy means:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux*.deb
```

Yes I did, must have hit Ctrl + x instead of Ctrl + c when copying the name of the file

Thanks chili555

---

### Post by linlinz on 2016-12-29
Thanks a lot for Chili555 and Jeremy! Everything works perfectly now

---

