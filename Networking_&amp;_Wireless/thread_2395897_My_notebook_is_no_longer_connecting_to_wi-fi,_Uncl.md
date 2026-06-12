---
title: "My notebook is no longer connecting to wi-fi, Unclaimed"
date: 2018-07-07
forum: Networking &amp; Wireless
---

### Post by jbrax2 on 2018-07-07
I have similar issue. This morning I installed software updates to Ubuntu 16.04 on Lenovo laptop and after requested reboot wifi would not reconnect. One similarity, my "lshw -c network" command also displays "network UNCLAIMED" for my wifi controller, although I have a different controller (Intel Wireless-N 7260). Laptop wifi works flawlessly when booted from Ubuntu LIVE 16.04 thumb drive, which seems to rule out laptop and network as part of issue. I believe wifi module is not loading into kernel at boot, but wifi firmware file (iwlwifi-7260-17.ucode) is present in /lib/firmware. I have run Wireless Script and have the text file, but may need help attaching it, if anyone is interested. I'm not a rank noob, but certainly far from guru. Any help would be appreciated. At this point my only obvious option is re-install and NEVER run another update.

---

### Post by jeremy31 on 2018-07-08
Split from another topic, If you have an ethernet connection try ```
cat wireless-info.txt | nc termbin.com 9999
```
Post the URL and that will be a link to the script results

---

### Post by jbrax2 on 2018-07-08
Jeremy - thank you for the respond. My wifi issue is still unsolved but I found a work-around. Laptop is single operating system & I had some difficulty getting to grub menu. But when I finally did, was able to boot 4.13 version of kernel and wifi works normally. Something in the software update yesterday morning disabled wifi in my 4.15 kernel, and I would still like to pursue a fix to 4.15 kernel. 

I ran Wireless Script (before installing pastebinit) and have text copy. With pastebinit installed, I see that I can run script again and have option of posting it. How would you like me to proceed? I guess I'll need to boot back into 4.15 kernel on laptop and connect to network with Ethernet, which is not a problem. Would you like me to run the cat command above or post information from Wireless Script or ... something else? Again, thank you for your help.

---

### Post by jeremy31 on 2018-07-08
Actually post results using 4.13 for ```
dpkg -l | grep linux | grep 4.15
```

---

### Post by jbrax2 on 2018-07-08
with 4.13 kernel booted:

$ dpkg -l | grep linux | grep 4.15
ii  linux-image-4.15.0-24-generic               4.15.0-24.26~16.04.1                         amd64        Signed kernel image generic
ii  linux-modules-4.15.0-24-generic             4.15.0-24.26~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-24-generic       4.15.0-24.26~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP

---

### Post by jbrax2 on 2018-07-08
with 4.13 kernel booted:

$ dpkg -l | grep linux | grep 4.15
ii  linux-image-4.15.0-24-generic               4.15.0-24.26~16.04.1                         amd64        Signed kernel image generic
ii  linux-modules-4.15.0-24-generic             4.15.0-24.26~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-24-generic       4.15.0-24.26~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP

my bad - double posted

---

### Post by jeremy31 on 2018-07-08
Try ```
sudo apt-get install --reinstall linux-modules-extra-4.15.0-24-generic
```
Then see if wifi works in 4.15

---

### Post by jbrax2 on 2018-07-08
wifi restored in 4.15 kernel. Thank you so much. I'll try to remember this if an update ever disables wifi again.

---

