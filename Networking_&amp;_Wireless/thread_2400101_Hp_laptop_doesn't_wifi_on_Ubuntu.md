---
title: "Hp laptop doesn't wifi on Ubuntu"
date: 2018-09-02
forum: Networking &amp; Wireless
---

### Post by tackskull on 2018-09-02
Hi there, I wrote another post time ago on the same issue happening on Manjaro linux, I wasn't able to let wifi card working on this HP laptop. Asking for help on the manjaro forum nobody was able to fix the problem, so after this I decided to install ubuntu on this laptop and try if my wifi card is supported, but after install I can see wifi still doesn't see any network. So I ask you please guys to help me make this pc work at least on this linux system.

```
tackskull@tackskull-HP-250-G4-Notebook-PC:~$ lspci -nnk | grep 0280 -A3
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be
tackskull@tackskull-HP-250-G4-Notebook-PC:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no 
```


Thanks everybody

---

### Post by tackskull on 2018-09-03
guys, nobody can help me?

---

### Post by jeremy31 on 2018-09-03
What kernel, post results from terminal for ```
uname -r; grep [[:alnum:]] /sys/module/rtl8723be/parameters/*
```

---

### Post by tackskull on 2018-09-03
```
~$ uname -r; grep [[:alnum:]] /sys/module/rtl8723be/parameters/*
4.15.0-33-generic
/sys/module/rtl8723be/parameters/ant_sel:0
/sys/module/rtl8723be/parameters/aspm:1
/sys/module/rtl8723be/parameters/debug_level:0
/sys/module/rtl8723be/parameters/debug_mask:0
/sys/module/rtl8723be/parameters/disable_watchdog:N
/sys/module/rtl8723be/parameters/fwlps:Y
/sys/module/rtl8723be/parameters/ips:Y
/sys/module/rtl8723be/parameters/msi:N
/sys/module/rtl8723be/parameters/swenc:N
/sys/module/rtl8723be/parameters/swlps:N
```

---

### Post by jeremy31 on 2018-09-03
What other kernels are installed ```
dpkg -l | grep linux-image-generic
```

---

### Post by tackskull on 2018-09-04
```
dpkg -l | grep linux-image-generic
ii  linux-image-generic                        4.15.0.33.35                        amd64        Generic Linux kernel image

```

---

### Post by tackskull on 2018-09-05
are you guys still there?

---

### Post by jeremy31 on 2018-09-05
Sorry, was doing some other research on this.  For a test ```
cd /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
sudo wget https://www.dropbox.com/s/qp9a7lmibu2gr1q/rtl8723be.ko
```
Reboot, check UEFI/BIOS to make sure Secure Boot is disabled, you could also check ```
mokutil --sb-state
```
See if wifi works

---

### Post by tackskull on 2018-09-06
```
:~$ cd /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
tackskull@tackskull-HP-250-G4-Notebook-PC:/lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be$ sudo wget https://www.dropbox.com/s/qp9a7lmibu2gr1q/rtl8723be.ko
[sudo] password for tackskull: 
--2018-09-07 02:13:26--  https://www.dropbox.com/s/qp9a7lmibu2gr1q/rtl8723be.ko
Resolving www.dropbox.com (www.dropbox.com)... 162.125.69.1, 2620:100:6025:1::a27d:4501
Connecting to www.dropbox.com (www.dropbox.com)|162.125.69.1|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: /s/raw/qp9a7lmibu2gr1q/rtl8723be.ko [following]
--2018-09-07 02:13:26--  https://www.dropbox.com/s/raw/qp9a7lmibu2gr1q/rtl8723be.ko
Reusing existing connection to www.dropbox.com:443.
HTTP request sent, awaiting response... 302 Found
Location: https://uc397b2b4f60ab4d1f3b9381bbe7.dl.dropboxusercontent.com/cd/0/inline/AP2rJ4mzqSfVd34m2mmnSvJVxA9al5Mbnw0_UFffZTB2T2yPFNJC-QluoY1l1ZZ0GvJyPl3ySRTJ6sfRts8RZC36jm6jinnGEyRENo3hBVYChM9OFjGqDcfjfTp9jJMcSlr9VhuE5vZRbctjxp26rTopCA622o1WxgZ7zpIxWc2VCkLnLQks79P6BdZcRlp0f3A/file [following]
--2018-09-07 02:13:26--  https://uc397b2b4f60ab4d1f3b9381bbe7.dl.dropboxusercontent.com/cd/0/inline/AP2rJ4mzqSfVd34m2mmnSvJVxA9al5Mbnw0_UFffZTB2T2yPFNJC-QluoY1l1ZZ0GvJyPl3ySRTJ6sfRts8RZC36jm6jinnGEyRENo3hBVYChM9OFjGqDcfjfTp9jJMcSlr9VhuE5vZRbctjxp26rTopCA622o1WxgZ7zpIxWc2VCkLnLQks79P6BdZcRlp0f3A/file
Resolving uc397b2b4f60ab4d1f3b9381bbe7.dl.dropboxusercontent.com (uc397b2b4f60ab4d1f3b9381bbe7.dl.dropboxusercontent.com)... 162.125.69.6, 2620:100:6025:6::a27d:4506
Connecting to uc397b2b4f60ab4d1f3b9381bbe7.dl.dropboxusercontent.com (uc397b2b4f60ab4d1f3b9381bbe7.dl.dropboxusercontent.com)|162.125.69.6|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: /cd/0/inline2/AP2jE4toq9wT8WqkYTouKZRGeh_aQHWlunX-QmDjOdKh27ywfHAE7RZR47AyXMsdIidvHz0P05iTbpSmD9hKc7qohVkQNKOCt8fXTc8mhVpseqLEA-ecSFEMcK_UUt0qhqNNAOmbkFnSV00ti-zpJYDE_oXy9Wl_Wq5Rw3cyX0eTjCD-gHpt0PQVAv4s4CG2-37aona1mnKew9CoA0TrhimEjyT78ZMA1DL_kRdasr7AYHIs9hHOBqetkHvs_Myet2oogd2_qVdNosKS6jz_L5XAsZPgEQJp8RS7hOhV4ndgbThywJe7acm90wf0HTxDxwpUGHJeIWC9C5rD-P7IJoXUgL_X44Db-8ghl7VKIyTW7tsNpCYSBMyFQ8Re_3EF1QIHMo8zDdu6YXKbSQDvo7K7cSvBijhamB9kY-VAOawQYYfmtwjqDDuP43GXn6T5_Yw/file [following]
--2018-09-07 02:13:28--  https://uc397b2b4f60ab4d1f3b9381bbe7.dl.dropboxusercontent.com/cd/0/inline2/AP2jE4toq9wT8WqkYTouKZRGeh_aQHWlunX-QmDjOdKh27ywfHAE7RZR47AyXMsdIidvHz0P05iTbpSmD9hKc7qohVkQNKOCt8fXTc8mhVpseqLEA-ecSFEMcK_UUt0qhqNNAOmbkFnSV00ti-zpJYDE_oXy9Wl_Wq5Rw3cyX0eTjCD-gHpt0PQVAv4s4CG2-37aona1mnKew9CoA0TrhimEjyT78ZMA1DL_kRdasr7AYHIs9hHOBqetkHvs_Myet2oogd2_qVdNosKS6jz_L5XAsZPgEQJp8RS7hOhV4ndgbThywJe7acm90wf0HTxDxwpUGHJeIWC9C5rD-P7IJoXUgL_X44Db-8ghl7VKIyTW7tsNpCYSBMyFQ8Re_3EF1QIHMo8zDdu6YXKbSQDvo7K7cSvBijhamB9kY-VAOawQYYfmtwjqDDuP43GXn6T5_Yw/file
Reusing existing connection to uc397b2b4f60ab4d1f3b9381bbe7.dl.dropboxusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 146262 (143K) [application/octet-stream]
Saving to: &#8216;rtl8723be.ko.1&#8217;

rtl8723be.ko.1      100%[===================>] 142,83K  --.-KB/s    in 0,02s   

2018-09-07 02:13:28 (6,53 MB/s) - &#8216;rtl8723be.ko.1&#8217; saved [146262/146262]

```


Thanks for your time!

I'vedone this and rebooted, nothing change.

---

### Post by tackskull on 2018-09-06
Secure boot is disabled already, I used all the code you gave me, I have rebooted, nothing change. I don't really know what is wrong with this laptop.

---

### Post by jeremy31 on 2018-09-07
One thing surprised me,it named the file rtl8723be.ko.1, so
```
cd /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
sudo mv rtl8723be.ko rtl8723be.ko.bak
sudo mv rtl8723be.ko.1 rtl8723be.ko
```
Reboot

---

### Post by tackskull on 2018-09-07
The strange thing is that Ubuntu is the third system I installed in this pc. First I installed Kubuntu and wifi was not working at the beginning, but asking on this forum seems that wifi card was just needing to be activated. Then at certain point wifi card stopped to work, so I tried to use Manjaro, but the issue wasn't able to be fixed. Then I tried with Ubuntu and the problem still here. Is that probably not a problem of system but something I must set from the pc's uefi/bios? I tried to see and wifi is abled in there.

---

### Post by tackskull on 2018-09-07
> **jeremy31 said:**
> One thing surprised me,it named the file rtl8723be.ko.1, so
```
cd /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
sudo mv rtl8723be.ko rtl8723be.ko.bak
sudo mv rtl8723be.ko.1 rtl8723be.ko
```
Reboot

Didt it, wifi still doesn't see any connection

---

### Post by jeremy31 on 2018-09-07
The RTL8723BE chipset works fine in Linux, at least with some kernels and the use of ant_sel=2 with some HP laptops because HP decided to only use one antenna wire instead of two.  The issue with 4.15.0-33 is that an upstream commit was included that messed up the antenna select feature

---

### Post by tackskull on 2018-09-07
So, what should I do now?

---

### Post by tackskull on 2018-09-07
> **jeremy31 said:**
> The RTL8723BE chipset works fine in Linux, at least with some kernels and the use of ant_sel=2 with some HP laptops because HP decided to only use one antenna wire instead of two.  The issue with 4.15.0-33 is that an upstream commit was included that messed up the antenna select feature

So, what shoul I do to fix this problem?

---

### Post by wildmanne39 on 2018-09-07
Please be patient we are all volunteers here from all over the world with lives, jobs and families and occasionally we need to sleep. You can bump your thread once every twelve hours if you do not receive a reply.

Thanks

---

### Post by tackskull on 2018-09-07
Yes I know perfectly and I say thanks you everybody, I'll do my best

---

### Post by jeremy31 on 2018-09-08
Download
[http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-headers-4.15.0-33_4.15.0-33.37~lp1788997_all.deb](http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-headers-4.15.0-33_4.15.0-33.37~lp1788997_all.deb)
[http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-image-unsigned-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb](http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-image-unsigned-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb)
[http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-modules-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb](http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-modules-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb)
[http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-modules-extra-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb](http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-modules-extra-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb)
Then in terminal, change into the directory and ```
sudo dpkg -i linux*.deb
```

---

### Post by tackskull on 2018-09-08
> **jeremy31 said:**
> Download
[http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-headers-4.15.0-33_4.15.0-33.37~lp1788997_all.deb](http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-headers-4.15.0-33_4.15.0-33.37~lp1788997_all.deb)
[http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-image-unsigned-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb](http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-image-unsigned-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb)
[http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-modules-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb](http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-modules-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb)
[http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-modules-extra-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb](http://kernel.ubuntu.com/~jsalisbury/lp1788997/linux-modules-extra-4.15.0-33-generic_4.15.0-33.37~lp1788997_amd64.deb)
Then in terminal, change into the directory and ```
sudo dpkg -i linux*.deb
```


I don't understand, I downloaded and installed all the links then what  you mean for "change into the directory"? Using that code it gave me an  error, what have I to do to?

---

### Post by chili555 on 2018-09-08
> **tackskull said:**
> I don't understand, I downloaded and installed all the links then what  you mean for "change into the directory"? Using that code it gave me an  error, what have I to do to?Where did the deb files download? Usually, downloads go to the aptly named folder Downloads. Check:```
cd ~/Downloads
ls | grep linux
```Are all the deb files there? If so, install them:```
sudo dpkg -i linux*.deb
```Reboot and tell us if the wireless is working.

---

### Post by tackskull on 2018-09-08
Woooww, wifi is finally working, I really thanks you guys, I can finally use my laptop to work, thaaaaannnnnkkkkksssss :) :) :)

---

### Post by chili555 on 2018-09-08
Awesome! Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

Thanks to jeremy31 for his research and solution for this difficult problem.

---

### Post by tackskull on 2018-09-08
> **jeremy31 said:**
> One thing surprised me,it named the file rtl8723be.ko.1, so
```
cd /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
sudo mv rtl8723be.ko rtl8723be.ko.bak
sudo mv rtl8723be.ko.1 rtl8723be.ko
```
Reboot

Hope this topic can help somebody else having problems with wifi.

Thank you soooo much Jeremy

---

### Post by jeremy31 on 2018-09-08
I hope this kernel issue is short lived

---

