---
title: "Dlink dwa182 detection problem in 18.04"
date: 2019-08-23
forum: Networking &amp; Wireless
---

### Post by daij163 on 2019-08-23
Hello, I have this wireless dongle DWA-182 version D1 that runs perfectly on my laptop running Ubuntu 14.04 but I can't seem to get it to work on a desktop running 18.04 that I just upgraded from 16.04.

When I run ^ lsusb ^, it is listed as 
Bus 002 Device 006: ID 2001:331c D-Link Corp.

I had looked up a couple of threads in the Forum that suggested the following and I ran the commands without error but the detection failure persists, i.e. under Settings/ Wi-fi, it says "No wi-fi adapter found".

```
sudo apt update
sudo apt install -y git
git clone [https://github.com/EntropicEffect/rtl8822bu.git](https://github.com/EntropicEffect/rtl8822bu.git)
cd rtl8822bu
make
sudo make install
sudo modprobe 88x2bu
```

I rebooted after running the commands, removed the dongle, plugged it back in and yet, no success so far.

I'd appreciate any advice to troubleshoot and resolve the problem please. Thank you!



P/S. I had originally tried to install the dongle under 16.04 and had made the mistake of running commands for rtl8812au. I had since removed the relevant files by running ^ sudo apt remove rtl8812au-dkms ^.

---

### Post by praseodym on 2019-08-23
[https://ubuntuforums.org/showthread.php?t=2394372&p=13776566#post13776566](https://ubuntuforums.org/showthread.php?t=2394372&p=13776566#post13776566)

Try this one instead

---

### Post by daij163 on 2019-08-23
Thank you, praseodym.

I actually tried this at 16.04. Of course it didn't work then. I can't recall what I did but I didn't manage to delete the dkms for this version.

Anyway, when I followed the steps, there was a fatal error since the files and settings already existed and no duplicates are allowed. I went through every step in any case and the DWA182 is unfortunately still not recognized properly.

Problem persisted, "No wi-fi adapter found." although the device is listed when I run ^ lsusb ^.

1. Does it make a difference when I didn't have the dongle plugged in when I ran the commands?

2. How do I delete all files, settings related to this and repeat the whole process from a "clean" slate?

Thanks again!

---

### Post by jeremy31 on 2019-08-23
```
cd rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044
git pull
```
That should update the code so you can try installing again

---

### Post by daij163 on 2019-08-23
Hello jeremy31. Thank you for your prompt reply.

I ran the commands and it says, "Already up to date." but no indication of "reset". Does this mean I'm good to repeat the process suggested by praseodym?


Update :

After I ran the commands suggested by jeremy31 above, I repeated the process suggested by praseodym in post #2. There are error messages, similar to what I encountered and described in post #3 above. The whole process can be viewed at

[https://pastebin.com/7yrjNtaX](https://pastebin.com/7yrjNtaX)

---

### Post by chili555 on 2019-08-23
Please confirm that the driver covers your exact device:```
modinfo 88x2bu | grep 331
```Load the driver and see if there are any errors or other interesting messages:```
sudo modprobe 88x2bu
```Finally, check the message log for messages:```
dmesg | grep -e rtl -e 88x2bu
```

---

### Post by daij163 on 2019-08-24
Hope this makes for interesting read and reveals more clues. :)

-desktop:~$ modinfo 88x2bu | grep 331
-desktop:~$ sudo modprobe 88x2bu
-desktop:~$ dmesg | grep -e rtl -e 88x2bu
[  790.194448] 88x2bu: loading out-of-tree module taints kernel.
[  790.195768] 88x2bu: module verification failed: signature and/or required key missing - tainting kernel
[  790.199786] RTW: rtl88x2bu v5.2.4.4_25643.20171212_COEX20171012-5044
[  790.199787] RTW: rtl88x2bu BT-Coex version = COEX20171012-5044
[  790.199825] usbcore: registered new interface driver rtl88x2bu

---

### Post by chili555 on 2019-08-27
> -desktop:~$ modinfo 88x2bu | grep 331No response means that the driver doesn't cover your exact device. Let's have a look at:```
sudo dkms status
modinfo 88x2bu | grep version 
```The version v5.3.1_27678.20180430_COEX20180427-5959 does cover your device.

---

### Post by daij163 on 2019-08-28
Much appreciated, chili555.

-desktop:~$ sudo dkms status
 [sudo] password for #######:  
 rtl88x2bu, 5.2.4.4, 4.15.0-58-generic, i686: installed
 rtl88x2bu, 5.2.4.4, 4.4.0-159-generic, i686: installed
 -desktop:~$ modinfo 88x2bu | grep version
 version:        v5.2.4.4_25643.20171212_COEX20171012-5044
 srcversion:     2D2C7268B8080EE9E2DEE32
 parm:           rtw_chip_version:int

---

### Post by chili555 on 2019-08-28
As we see, you have the 5.2.xx version installed. It doesn't cover your device. You need 5.3.1.xx.

Please do:```

sudo dkms remove rtl88x2bu/5.2.4.4 --all
```And now install the newer version:```

git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.git

```If it is already on your system, that's fine, just continue:```
cd rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
```Make sure the version you have is fully updated:```
git pull

```Now install it:```

VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu

```Your wireless should now be working.

---

### Post by daij163 on 2019-08-28
Worked like a charm! I'm using the device to connect and posting this message.

Utmost respect and gratitude to you, chili555.

Thank you, praseodym and jeremy31, for chipping in too.

---

