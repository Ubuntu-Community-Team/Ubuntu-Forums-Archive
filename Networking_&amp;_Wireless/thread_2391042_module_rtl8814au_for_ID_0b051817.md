---
title: "module rtl8814au for ID 0b05:1817"
date: 2018-05-05
forum: Networking &amp; Wireless
---

### Post by sacarde on 2018-05-05
hi,
   I found howto build this module (asus wireless) for ubuntu16.04
but no one for ubuntu-18.04 (kernel 4.15.0)

can you help me?

or is there a module dkms ?





thank you

---

### Post by jeremy31 on 2018-05-05
Moved to networking and wireless
I just found one that installs
```
sudo apt-get update && sudo apt-get install git dkms
git clone https://github.com/zebulon2/rtl8814au.git
cd rtl8814au
gedit dkms.conf
```
Replace line 1 MAKE="'make'" with
```
MAKE="'make' all KVER=${kernelver}"
```
save and exit gedit, then
```
cd 
sudo dkms add ./rtl8814au
sudo dkms install rtl8814au/4.3.21
```
Reboot

The edit is needed to dkms.conf so that dkms will build the module against the correct kernel for kernel updates

---

### Post by sacarde on 2018-05-05
wow !! it works

thank you  jeremy31

---

