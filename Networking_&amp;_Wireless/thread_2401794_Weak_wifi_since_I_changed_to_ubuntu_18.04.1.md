---
title: "Weak wifi since I changed to ubuntu 18.04.1"
date: 2018-09-22
forum: Networking &amp; Wireless
---

### Post by albertodgar on 2018-09-22
Hello, recently I changed from Windows to ubuntu . Since then I have a very bad wifi connection. It's slow, and it dissapears constantly. Also, my computer doesn't detect any signal if I'm out of the room.

I've tried this solution [https://ubuntuforums.org/showthread.php?t=1899391](https://ubuntuforums.org/showthread.php?t=1899391) but it doesn't work for me (I've changed gksu for admin:\\ because I've read that it's the way to do it in this version).

I'would highly appreciate if someone could help me.

---

### Post by chili555 on 2018-09-22
Do you have a Broadcom wireless device as in the thread you linked?

Please run and post:```
lspci -nnk | grep 0280 -A3
```

---

### Post by albertodgar on 2018-09-23
> Do you have a Broadcom wireless device as in the thread you linked?

I think I don't.

After runing the code I get this

> 
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be


---

### Post by chili555 on 2018-09-23
> Do you have a Broadcom wireless device as in the thread you linked?
I think I don't.

After runing the code I get thisYou are not the first, last or only new Ubuntuan who applies Broadcom fixes and Intel fixes and Atheros fixes to their Realtek wireless setup, or vice versa, and then is disappointed when it doesn't work. 

----------

RANT TO SEARCHERS: If you don't know what your device is, don't blindly apply random fixes. They likely will do nothing at all but waste time. Find out what device you have with:```
lspci -nnk
```Or, if it's a USB device:```
lsusb
```

----------

As to your specific case, This specific device and the latest kernel are the subject of a bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788997](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788997)

I suggest that you try the following steps:```
sudo modprobe -r rtl8723be 
sudo modprobe rtl8723be ant_sel=1
```Any improvement?

If not, repeat the process with ant_sel=2. Any improvement?

If not, and I suspect not, we refer to the bug report at posts #25 and following:> I've tested with the kernel as recommended and suggest in #25. Wifi with rtl8723b3 works again (like a charm). However, ant_sel must be set to 1 (ant_sel=1) as opposed to kernel 4.15.0-32, which required ant_sel to be set to 2 (ant_sel=2). (e.g sudo modprobe rtl8723be ant_sel=1 vs. sudo modprobe rtl8723be ant_sel=2).At post #32, we see that kernel version 4.17-rc4 works well.

Therefor, I suggest that, if and only if the ant_sel steps don't work, then install the kernel and associated packages:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc4/linux-headers-4.17.0-041700rc4_4.17.0-041700rc4.201806041713_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc4/linux-headers-4.17.0-041700rc4_4.17.0-041700rc4.201806041713_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc4/linux-headers-4.17.0-041700rc4-generic_4.17.0-041700rc4.201806041713_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc4/linux-headers-4.17.0-041700rc4-generic_4.17.0-041700rc4.201806041713_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc4/linux-image-unsigned-4.17.0-041700rc4-generic_4.17.0-041700rc4.201806041713_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc4/linux-image-unsigned-4.17.0-041700rc4-generic_4.17.0-041700rc4.201806041713_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc4/linux-modules-4.17.0-041700rc4-generic_4.17.0-041700rc4.201806041713_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc4/linux-modules-4.17.0-041700rc4-generic_4.17.0-041700rc4.201806041713_amd64.deb)

I suggest that you download them all. By default, downloads go to the folder Downloads. Open a terminal and do:```
cd ~/Downloads
sudo dpkg -i linux*.deb
```Reboot.

---

### Post by albertodgar on 2018-09-23
Thanks a lot. It worked for me!!

---

### Post by chili555 on 2018-09-23
Awesome! Glad it&#8217;s working.

Did you have to set ant_sel? We can make it persistent so you needn&#8217;t redo it after every reboot.

---

### Post by albertodgar on 2018-10-02
oh sorry I didn't see it until now. Yes, it was much better with ant_sel=2. I we can make it persistent it would be awesome.

---

### Post by chili555 on 2018-10-02
> **albertodgar said:**
> oh sorry I didn't see it until now. Yes, it was much better with ant_sel=2. I we can make it persistent it would be awesome.We'll create a file that tells the system to load the driver with the ant_sel parameter set for you. From the terminal:```
sudo -i
echo "options rtl8723be ant_sel=2"  >  /etc/modprobe.d/rtl8723be.conf
exit
```You should be all set.

---

### Post by adarshin on 2018-10-02
It worked for me. Downloaded all the 4 files and installed it. Now it's fine. Thanks for the share Bro.

---

### Post by albertodgar on 2018-10-02
Thanks a lot. It was really helpful.

---

