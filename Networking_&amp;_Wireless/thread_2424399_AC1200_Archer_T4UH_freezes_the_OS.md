---
title: "AC1200 Archer T4UH freezes the OS"
date: 2019-08-08
forum: Networking &amp; Wireless
---

### Post by ezlar on 2019-08-08
I have followed the instructions listed in [https://ubuntuforums.org/showthread.php?t=2340769](https://ubuntuforums.org/showthread.php?t=2340769).
This successfully allows the wireless adapter to be recognized, however when I try to connect to a network it will either fail to connect, or alternatively the whole system will hang and require a reboot. 

Extremely rarely and in ways I have not been able to reproduce, it will sometimes successfully connect to a network, but not allow me to switch to any other network. 
My suspicions point me towards some sort of driver issue, potentially a conflicting one? But I know too little about this to be sure. 
I would greatly appreciate any assistance with this issue!

---

### Post by chili555 on 2019-08-08
Let's gather some basic diagnostics:```
lsusb
sudo dkms status
```Thanks.

---

### Post by ezlar on 2019-08-08
Thanks Chili!

lsusb:
```
Bus 006 Device 002: ID 2357:0103  
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 1532:0043 Razer USA, Ltd 
Bus 005 Device 003: ID 2516:004d  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1038:1294 SteelSeries ApS 
Bus 003 Device 003: ID 1038:1290 SteelSeries ApS 
Bus 003 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0930:1400 Toshiba Corp. Memory Stick 2GB
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 045e:02fe Microsoft Corp. 
Bus 001 Device 003: ID 1c9e:f133 OMEGA TECHNOLOGY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The first entry is the adapter. 

dkms status:
```
rtl8812au, 4.3.8.12175.20140902+dfsg: added
rtl8812au, 5.2.20.2, 5.0.0-21-generic, x86_64: installed
system76, 1.0.4~1561669629~18.04~6ea4ee8, 5.0.0-21-generic, x86_64: installed
system76-io, 1.0.1~1559663713~18.04~ea5f61a, 5.0.0-21-generic, x86_64: installed
xpad, 0.4, 5.0.0-21-generic, x86_64: installed

```

I removed 4.3.8 in case that was causing conflicts and re-installed 5.2, but the issue persists. 
The updated dkms status:
```
rtl8812au, 5.2.20.2, 5.0.0-21-generic, x86_64: installed
system76, 1.0.4~1561669629~18.04~6ea4ee8, 5.0.0-21-generic, x86_64: installed
system76-io, 1.0.1~1559663713~18.04~ea5f61a, 5.0.0-21-generic, x86_64: installed
xpad, 0.4, 5.0.0-21-generic, x86_64: installed

```

---

### Post by chili555 on 2019-08-08
So far, so good. You have installed, apparently correctly, the correct driver for the device. Let's see what the message log has to say:

```
dmesg | grep -ie rtl -e 8812
sudo modprobe 8812au
```

---

### Post by ezlar on 2019-08-08
No hits on dmsg, modprobe returns this : 
```
modprobe: FATAL: Module 8812au not found in directory /lib/modules/5.0.0-21-generic

```
The contents of the directory:
```
ls /lib/modules/5.0.0-21-generic/
build          modules.alias.bin    modules.dep.bin  modules.symbols
initrd         modules.builtin      modules.devname  modules.symbols.bin
kernel         modules.builtin.bin  modules.order    updates
modules.alias  modules.dep          modules.softdep  vdso

```

---

### Post by chili555 on 2019-08-08
It is probably /lib/modules/5.0.0-23-generic/updates/dkms/8812au.ko or some such.

Please try:```
sudo modprobe rtl8812au
```Fascinating....

---

### Post by ezlar on 2019-08-08
Much of the same for modprobe:

```
sudo modprobe rtl8812au
modprobe: FATAL: Module rtl8812au not found in directory /lib/modules/5.0.0-21-generic

```

Checked out the directory, I assume 88XX is a valid generalization? 
```
lib/modules/5.0.0-21-generic/updates/dkms$ ls
88XXau.ko  system76-io.ko  system76.ko  xpad.ko



```

---

### Post by chili555 on 2019-08-08
88XXau.ko??  How interesting. Tell us more:```
modinfo 88XXau | grep 0103
sudo modprobe 88XXau
dmesg | grep 88XX
```Off for the evening; I'll check back tomorrow.

---

### Post by ezlar on 2019-08-08
```

modinfo 88XXau | grep 0103
alias:          usb:v2357p0103d*dc*dsc*dp*ic*isc*ip*in*

```
modprobe and dmesg both come up blank

---

### Post by chili555 on 2019-08-09
Let's try: ```
dmesg | grep -e 88XX -e wlx
lspci -nnk | grep 0280 -A3
```Good morning!

---

### Post by ezlar on 2019-08-09
Good morning Chili!
Both commands also come up blank.
I should note that the device is unplugged when I run these, because having it plugged in will lead to an imminent OS freeze.
Does that make a difference?
Thanks

---

### Post by chili555 on 2019-08-10
> 
I should note that the device is unplugged when I run these, because having it plugged in will lead to an imminent OS freeze.
Does that make a difference?
It will unfortunately be impossible to troubleshoot unless the device is inserted, we load the module and it crashes. 

If it were possible without the device inserted, I'd simply run the commands on my own computer and tell you what is wrong and how to fix it. That would be a pretty neat trick, wouldn't it?

Here is what I suggest that you do. Open a terminal and run:```
tail -f var/log/syslog
```Make a note of the timestamp of the very last entry. For example, here is the output from my computer:

```
Aug 10 10:50:15 T440p org.gnome.Shell.desktop[2278]: # watch_established: "/org/gnome/terminal/legacy/" (establishing: 0)

```So, in my example, I'd make note of *Aug 10 10:50:15.*

Now, get out of tail with Crtl+c. Now insert the device and let it crash. Remove the device and reboot. Now check the log:```
less /var/log/syslog
```Scroll down with the arrow keys to the timestamp you noted and copy and paste the next following 30 or so lines here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com) I suspect that we'll see the fault and can then correct it.

Get out of less with q.

---

### Post by ezlar on 2019-08-14
Hi Chili!

Thank you for your reply. 
My apologies for not having the device inserted. 
I have been busy lately so I haven't had a chance to gather and post the information, but I will be sure to do so tomorrow!
Thanks.

---

### Post by ezlar on 2019-08-16
Thank you for your patience Chili. 
There may be a few more lines that what is necessary in this paste, but it did seem to refer to the adapter for quite some time. 
I hope it makes more sense to you than it did to me!
[https://paste.ubuntu.com/p/wJyMkKsYBQ/](https://paste.ubuntu.com/p/wJyMkKsYBQ/)
Kind regards,
Ezlar

---

