---
title: "Sitecom N300 WLA-4001 (RTL8192cu) Ubuntu 13.10"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by martijn5 on 2014-02-28
hello guys,

I trying to get Sitecom N300 WLA-4001 (RTL8192cu) work on Ubuntu 13.10 

I follow this tread: [http://ubuntuforums.org/showthread.php?t=2070697](http://ubuntuforums.org/showthread.php?t=2070697)
 after i copy the file (**rtl8192cufw.bin**) to directory (**/lib/firmware/RTL8192CU/**)

i try to: sudo modprobe rtl8192cu but i get a error
> sh: 1: cannot create /sys/bus/usb/drivers/rtl819cu/new_id: Directory nonexistent
libkmod: ERROR ../libkmod/libkmod-module.c:925 command_do: Error running install command for rtl8192cu
ERROR: could not insert 'rtl8192cu': Unknown symbol in module, or unknown parameter (see dmesg)
 



please help!

---

### Post by martijn5 on 2014-02-28
I ]

---

### Post by chili555 on 2014-02-28
> **martijn5 said:**
> I ]Yes?? Did you get it fixed? You probably don't need the $CMDLINE_OPTS step in 13.10.

---

### Post by martijn5 on 2014-03-01
Tanks chili555,

I am very new in the linux environment, just a noobie

so if i am right; i have to delete $CMDLINE_OPTS in the step :p

but when i follow the other step:
> sudo modprobe rtl8192cu

he doesn't give errors, after this i five the computer a restart. Then i do this > iwconfig only the card is not found?!?!

---

### Post by praseodym on 2014-03-01
Hi,

update the driver according to:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot. The new module name is **8192cu** (without 'rtl')

---

### Post by martijn5 on 2014-03-01
> sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf

so i am right, after this its working so i can try iwconfig

---

### Post by chili555 on 2014-03-01
> so i am right, after this its working so i can try iwconfig Yes. And does iwconfig see your device? Can you connect?

---

### Post by martijn5 on 2014-03-02
NOO:confused:
> 
eth0      no wireless extensions.

lo        no wireless extensions.



is it maybe important to say, that i use vmware machine?!? :$

i am sorry for not saying

---

### Post by chili555 on 2014-03-02
> is it maybe important to say, that i use vmware machine?!? :$ Indeed it is important to get the facts right from the start. Networking is generally handled a bit differently in a virtual machine. This may be helpful:  [https://www.vmware.com/support/ws55/doc/ws_net_configurations_changing_bridged_windows.html](https://www.vmware.com/support/ws55/doc/ws_net_configurations_changing_bridged_windows.html)

---

### Post by xp15 on 2014-04-18
Well, It worked now, the clone. I will keep fixing it! Thank!

---

### Post by xp15 on 2014-04-22
How can I remove and reinstall?
I tried doing it again, but I get "sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git".
I tried something else, but now things are less good than before. I miss the old condition...

---

### Post by chili555 on 2014-04-22
> **xp15 said:**
> 
I tried something else, In order to help you fix it, we need to know what 'something else' you tried.

---

