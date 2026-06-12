---
title: "Suddenly Lost Wifi"
date: 2018-09-29
forum: Networking &amp; Wireless
---

### Post by ricky25 on 2018-09-29
Hi, turned on my Intel nuc today, no wifi showing on Ubuntu mate 18.04 , never had any problems before, using wired at moment. I did recently plug in a usb hub but removing it has no effect.

Wifi also gone from my linux mint 18.04 installed on different partition as dual boot, does this seem to be hardware or kernel. Also if I click Enable Networking to stop the wired connection I see the wireless symbol just like before I plugged in my ethernet cable in, can I use this to toggle between wireless and wired to save me unplugging my ethernet cable to check the wireless connection.

Tried updating firmware to, no change, just not seeing any wireless networks, thank you.

---

### Post by jeremy31 on 2018-09-29
Moved to Network & Wireless
Please post results from terminal for ```
dpkg -l | egrep 'linux-image|linux-modules-extra; lspci -nnk | grep -iA3 net
```

---

### Post by ricky25 on 2018-09-29
Thanks for reply, run script, no output, blank.

---

### Post by jeremy31 on 2018-09-29
Press CTRL + c in terminal and do ```
dpkg -l | egrep 'linux-image|linux-modules-extra'; lspci -nnk | grep -iA3 net
```

---

### Post by ricky25 on 2018-09-29
Would the [COLOR=#000000][FONT=&quot]sudo apt install --reinstall linux-modules, kernel version, command help etc, thanks.[/FONT][/COLOR]

---

### Post by ricky25 on 2018-09-29
ricky@Mate:~$ dpkg -l | egrep 'linux-image|linux-modules-extra'; lspci -nnk | grep -iA3 net
rc  linux-image-4.15.0-20-generic         4.15.0-20.21                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-23-generic         4.15.0-23.25                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-34-generic         4.15.0-34.37                        amd64        Signed kernel image generic
ii  linux-image-generic                   4.15.0.34.36                        amd64        Generic Linux kernel image
rc  linux-modules-extra-4.15.0-20-generic 4.15.0-20.21                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-23-generic 4.15.0-23.25                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-34-generic 4.15.0-34.37                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Intel Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [8086:2067]
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by ricky25 on 2018-09-29
ricky@Mate:~$ cdpkg -l | egrep 'linux-image|linux-modules-extra'; lspci -nnk | grep -iA3 net


Command 'cdpkg' not found, did you mean:


  command 'dpkg' from deb dpkg


Try: sudo apt install <deb name>


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Intel Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [8086:2067]
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by ricky25 on 2018-09-29
ricky@Mate:~$ c ricky@Mate:~$ cdpkg -l | egrep 'linux-image|linux-modules-extra'; lspci -nnk | grep -iA3 net
c: command not found
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Intel Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [8086:2067]
	Kernel driver in use: r8169
	Kernel modules: r8169
ricky@Mate:~$ 
ricky@Mate:~$ Command 'cdpkg' not found, did you mean:
Command: command not found
ricky@Mate:~$ 
ricky@Mate:~$   command 'dpkg' from deb dpkg
dpkg: error: need an action option


Type dpkg --help for help about installing and uninstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
ricky@Mate:~$ 
ricky@Mate:~$ Try: sudo apt install <deb name>
bash: syntax error near unexpected token `newline'
ricky@Mate:~$ 
ricky@Mate:~$ 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
bash: syntax error near unexpected token `('
ricky@Mate:~$ Subsystem: Intel Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [8086:2067]
Subsystem:: command not found
ricky@Mate:~$ Kernel driver in use: r8169
Kernel: command not found
ricky@Mate:~$ Kernel modules: r8169
Kernel: command not found
ricky@Mate:~$

---

### Post by jeremy31 on 2018-09-29
What about results for ```
lsusb
```

---

### Post by ricky25 on 2018-09-29
ricky@Mate:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 8087:0aa7 Intel Corp. 
Bus 001 Device 005: ID 0480:a200 Toshiba America Inc 
Bus 001 Device 007: ID 0781:5581 SanDisk Corp. Ultra
Bus 001 Device 004: ID 2109:2813 VIA Labs, Inc. 
Bus 001 Device 003: ID 045e:07f8 Microsoft Corp. Wired Keyboard 600 (model 1576)
Bus 001 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2018-09-29
Is it somehow disabled in BIOS settings?

---

### Post by ricky25 on 2018-09-29
Thanks for your help, have to go out, will check replies tonight and do some more research, I think an update might be the culprit or my new usb 3 hub.

---

### Post by ricky25 on 2018-09-29
Will check bios, have to connect to different monitor to view bios, I haven't changed any bios settings, been working fine. Will try the intel forum for possible hardware failure or conflicts with other hardware, thanks again. Will post back tomorrow.

---

