---
title: "No Wifi on Ubuntu 12.04 on HP Pavilion notebook."
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by tat3 on 2014-02-03
I am quite new to all of this so let me please apoligise if i sound stupid, but i hate the new windows 8 that came with my laptop and would love to get back on Ubuntu. I had Ubuntu 12.10 installed on my last laptop and it ran smoothly with no problems, ive upgraded and had nothing but problems since. I have finally managed to install Ubuntu 12.04, after trying nearly every other Ubuntu distro possible, it seems i cant use the wifi. I have tried for days searching round the internet and trying to install various drivers, but to no avail. Wired connection works fine, and the wifi works on windows 8 (much to my frustration). If you could help it would be much apprciated. So, this is my wifi card (I think)

```
lspci -nn | grep 0200
```

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)

---

### Post by praseodym on 2014-02-03
Hi,

thats the LAN card. Lets check:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
pccardctl info
iwconfig
rfkill list
lsmod
```

---

### Post by tat3 on 2014-02-03
Hi thanks for the reply =]!! 

Linux Tat 3.8.0-35-generic #52~precise1-Ubuntu SMP Thu Jan 30 17:27:28 UTC 2014 i686 i686 i386 GNU/Linux
tat@Tat:~$ lspci -nnk | grep -iA2 net
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Hewlett-Packard Company Device [103c:2163]
    Kernel modules: r8169
tat@Tat:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 005: ID 0bb4:0ffe High Tech Computer Corp. Desire HD (modem mode)
Bus 002 Device 003: ID 064e:c33e Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
tat@Tat:~$ pccardctl info
tat@Tat:~$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

tat@Tat:~$ rfkill list
tat@Tat:~$ lsmod

---

### Post by praseodym on 2014-02-03
Install the driver via LAN:
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic-lts-raring
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```Reboot.

Dont remove the driver folder, after a kernel upgrade you need to compile again:
```

cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
make clean
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by tat3 on 2014-02-03
when i rebooted it said there had been an internal error, but it wouldnt let me copy the details, i went ahead and tried to compile it again anyway:

tat@Tat:~$ cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
bash: cd: rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013: No such file or directory
tat@Tat:~$ make clean
make: *** No rule to make target `clean'. Stop.
tat@Tat:~$ make
make: *** No targets specified and no makefile found. Stop.
tat@Tat:~$ sudo make install
[sudo] password for tat: 
Sorry, try again.
[sudo] password for tat: 
make: *** No rule to make target `install'. Stop.

---

### Post by tat3 on 2014-02-03
I tried again, this time there was no error but still got the same outcome

---

### Post by praseodym on 2014-02-04
Try this one instead:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/38/34/5443987-rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patc.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patc.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched/
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot.

---

### Post by Mark_Wolford on 2014-02-05
Dear Sir, Thank you for the fix.

---

### Post by praseodym on 2014-02-06
This one is needed to be recompiled, too, after a kernel upgrade. Similar as above.

---

### Post by cjhabs on 2014-02-06
I have an HP Pavilion dv5 with a Broadcom wireless card which I now have working but takes a lot of fiddling.
I purchased this from Amazon for $11  because it is compatible with Linux out of the box:
[http://www.amazon.com/gp/product/B00762YNMG/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00762YNMG/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1)
It has worked with every distro I have tried so far out of the box - just a suggestion to make life easier. It is a small USB device that you don't even notice is there!

---

### Post by tat3 on 2014-02-06
Thank you!!!! what should i change the name of the thread to so other users can find it =]

---

