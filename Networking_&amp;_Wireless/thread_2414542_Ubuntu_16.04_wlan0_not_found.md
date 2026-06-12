---
title: "Ubuntu 16.04 wlan0 not found"
date: 2019-03-12
forum: Networking &amp; Wireless
---

### Post by spec123 on 2019-03-12
Hi, I am new to ubuntu. I have dual boot my laptop with windows. My laptop is Asus-x555l. Currently I am using the net through etherenet but I can not use the wifi as it does not appear. I can use the wifi in my windows. I followed the link _[https://ubuntuforums.org/showthread.php?t=2239747](https://ubuntuforums.org/showthread.php?t=2239747)_ to solve my issue. But it is for ubuntu 14.04. I am adding my ifconfig info below as attachment  for your consideration. please help. thanks

---

### Post by jeremy31 on 2019-03-12
Moved to Networking, see the wireless script link in my signature and post results

---

### Post by chili555 on 2019-03-12
> **jeremy31 said:**
> Moved to Networking, see the wireless script link in my signature and post resultsYes, indeed. We need a full diagnostic work-up.

---

### Post by spec123 on 2019-03-13
Hi, I did both 
```


sudo apt update
sudo apt dist-upgrade


```

then reboot but still no wifi . then I did 

```

sudo apt install pastebinit


```

that resulted in the terminal following: 
```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libjansson4 libvdpau1 libxnvctrl0
  linux-headers-4.15.0-29 linux-headers-4.15.0-29-generic
  linux-image-4.15.0-29-generic linux-modules-4.15.0-29-generic
  linux-modules-extra-4.15.0-29-generic mesa-vdpau-drivers nvidia-prime
  nvidia-settings screen-resolution-extra vdpau-driver-all
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  pastebinit
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.6 kB of archives.
After this operation, 160 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 pastebinit all 1.5-1 [14.6 kB]
Fetched 14.6 kB in 0s (15.1 kB/s)   
Selecting previously unselected package pastebinit.
(Reading database ... 282425 files and directories currently installed.)
Preparing to unpack .../pastebinit_1.5-1_all.deb ...
Unpacking pastebinit (1.5-1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up pastebinit (1.5-1) ...


```

After that I ran the script  and did yes to post on default pastebinit. It gives the link [U][http://paste.ubuntu.com/p/t9cwYgmw7w/](http://paste.ubuntu.com/p/t9cwYgmw7w/).

[/U]please have a look and let me know what should I do next.



 Sorry I am new to these things. 
Thank you so much for your responses

---

### Post by jeremy31 on 2019-03-13
Do ```
sudo apt install git dkms build-essential
git clone https://github.com/neurobin/MT7630E.git
sudo dkms add ./MT7630E
sudo dkms install mt7630e/2.1.0
```
Reboot

---

### Post by spec123 on 2019-03-13
```

git clone https://github.com/neurobin/MT7630E.git


```

results
```


fatal: destination path 'MT7630E' already exists and is not an empty directory.


```

thanks

---

### Post by jeremy31 on 2019-03-13
Try ```
sudo dkms add ./MT7630E
sudo dkms install mt7630e/2.1.0
```

---

### Post by spec123 on 2019-03-13
It worked! Thank you very much jeremy31! After running 
```

sudo dkms add ./MT7630E
sudo dkms install mt7630e/2.1.0

```

I rebooted and the wifi is working fine! Thank you so much! 
Do you have any suggestion for me so that the wifi does not go away again?or it will be okay from now?

Thank you again

---

