---
title: "Lubuntu. Can't install RTL8188C_8192C"
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by jian3 on 2014-10-06
I have got some problem when I was installing RTL8188C_8192C 
I need help. Thanks
```

/home/jian/Scrivania/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:637:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_sreset;
       ^
/home/jian/Scrivania/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c: At top level:
/home/jian/Scrivania/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:999:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/home/jian/Scrivania/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:999:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/home/jian/Scrivania/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [_module_/home/jian/Scrivania/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-36-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


```

---

### Post by praseodym on 2014-10-06
Try this one instead:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by jian3 on 2014-10-07
thanks for answering.
I tried this code,but it still can't install. and have same errors.

---

### Post by praseodym on 2014-10-07
Please show
```

lsusb
lsmod
```with the stick plugged

---

