---
title: "How do I claim &quot;unclaimed network&quot;?"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by Mk147 on 2014-03-26
hey chili555..can u help me plzz,i have [same problem]("http://ubuntuforums.org/showthread.php?t=1314693&page=5") with my wifi card is unclaimed ...

code:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]uname -a
Linux Mk147 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux[/TD]
[/TR]
[/TABLE]

code:[TABLE="class: outer_border, width: 500"]
[TR]
[TD]*-network UNCLAIMED
       description: Network controller
       product: MEDIATEK Corp.
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
[/TD]
[/TR]
[/TABLE]

code:
    Network controller [0280]: MEDIATEK Corp. Device [14c3:7630]
    Subsystem: Hewlett-Packard Company Device [103c:197c]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at b0600000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: ndiswrappe

---

### Post by chili555 on 2014-03-26
Please provide more details:```
lspci -nn | grep 0280
```Thanks.

---

### Post by Mk147 on 2014-03-26
code:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]04:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7630]
[/TD]
[TD][/TD]
[/TR]
[/TABLE]


thank you chili

---

### Post by Mk147 on 2014-03-26
can anyone help please

---

### Post by chili555 on 2014-03-26
> **Mk147 said:**
> can anyone help pleaseI'm sorry; they make me lay down the keyboard and eat and sleep once in a while.

I have done a lengthy search for your device and found that there is a driver for kernel version 3.5 only: [https://github.com/anthonywong/mt7630](https://github.com/anthonywong/mt7630) Also see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146)

You are running kernel 3.11.0-xx. I tried to compile this driver and failed. I know of no driver for your device. You could install a 3.5 kernel and try it or invest US$10-15 for a USB wireless until a driver is developed. I wish I had a better answer to report.

---

### Post by Mk147 on 2014-03-26
loooool :P, no problem man and thank you so much for your effort , can you tell me how to install kernel 3.5 or give a link to follow 

thanx again chili555

---

### Post by chili555 on 2014-03-26
You might try this: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-3.5.0-24-generic_3.5.0-24.37_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-3.5.0-24-generic_3.5.0-24.37_amd64.deb)

You also need headers: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.5.0-24-generic_3.5.0-24.37_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.5.0-24-generic_3.5.0-24.37_amd64.deb)

Download them to your desktop and install:```
cd ~/Desktop
sudo dpkg -i linux*.deb
```Assuming there are no errors or missing dependencies, reboot. Interrupt the boot process by pressing the right Shift key until you see the GRUB menu: [http://3.bp.blogspot.com/-_ZHS9rYL2Lg/UG4ZDAr_-9I/AAAAAAAAFzU/yfKqJwaw7-o/s1600/ubuntu1210-grubbootmenu.jpg](http://3.bp.blogspot.com/-_ZHS9rYL2Lg/UG4ZDAr_-9I/AAAAAAAAFzU/yfKqJwaw7-o/s1600/ubuntu1210-grubbootmenu.jpg) Select Advanced Options and arrow down to the 3.5.0-24 kernel. Press Enter and boot into it. Now open a terminal and do:```
sudo apt-get install --reinstall build-essential
sudo apt-get install git
git clone https://github.com/anthonywong/mt7630.git
cd mt7630
sudo chmod +x build.sh
sudo ./build.sh
```It should install an updated driver rt2800pci; load it:```
sudo modprobe rt2800pci
```I haven't the device, so I can't test further. Please post any errors or snags if you see them.

---

### Post by Mk147 on 2014-03-26
tried to install .deb but no luck

[TABLE="width: 500"]
[TR]
[TD](Reading database ... 231531 files and directories currently installed.)
Preparing to replace linux-headers-3.5.0-24-generic 3.5.0-24.37 (using linux-headers-3.5.0-24-generic_3.5.0-24.37_amd64.deb) ...
Unpacking replacement linux-headers-3.5.0-24-generic ...
Preparing to replace linux-image-3.5.0-24-generic 3.5.0-24.37 (using linux-image-3.5.0-24-generic_3.5.0-24.37_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.5.0-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
dpkg: dependency problems prevent configuration of linux-headers-3.5.0-24-generic:
 linux-headers-3.5.0-24-generic depends on linux-headers-3.5.0-24; however:
  Package linux-headers-3.5.0-24 is not installed.

dpkg: error processing linux-headers-3.5.0-24-generic (--install):
 dependency problems - leaving unconfigured
Setting up linux-image-3.5.0-24-generic (3.5.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.5.0-24.37 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.5.0-24.37 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-24-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-24-generic (x86_64)
Consult /var/lib/dkms/ndiswrapper/1.58/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found initrd image: /boot/initrd.img-3.5.0-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Errors were encountered while processing:
 linux-headers-3.5.0-24-generic

[/TD]
[/TR]
[/TABLE]

---

### Post by chili555 on 2014-03-26
I would try:```
sudo apt-get purge ndiswrapper*

```Then try again:```
sudo dpkg -i linux-headers*.deb
```How about now?

---

### Post by Mk147 on 2014-03-26
still error :(

code:
```
Reading database ... 228535 files and directories currently installed.)
Preparing to replace linux-headers-3.5.0-24-generic 3.5.0-24.37 (using linux-headers-3.5.0-24-generic_3.5.0-24.37_amd64.deb) ...
Unpacking replacement linux-headers-3.5.0-24-generic ...
dpkg: dependency problems prevent configuration of linux-headers-3.5.0-24-generic:
 linux-headers-3.5.0-24-generic depends on linux-headers-3.5.0-24; however:
  Package linux-headers-3.5.0-24 is not installed.

dpkg: error processing linux-headers-3.5.0-24-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.5.0-24-generic
```

---

### Post by chili555 on 2014-03-26
Go get it: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.5.0-24_3.5.0-24.37_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.5.0-24_3.5.0-24.37_all.deb) And install it:```
sudo dpkg -i linux-headers*.deb
```

---

### Post by Mk147 on 2014-03-26
[B]ok no error this time :D .. i download it to my desktop ,cd desktop

code:
```
electing previously unselected package linux-headers-3.5.0-24.
(Reading database ... 219966 files and directories currently installed.)
Unpacking linux-headers-3.5.0-24 (from linux-headers-3.5.0-24_3.5.0-24.37_all.deb) ...
Setting up linux-headers-3.5.0-24 (3.5.0-24.37) ...
```

---

### Post by chili555 on 2014-03-26
Now I suggest you reboot into 3.5.0-24 as I outlined above and proceed.

---

### Post by Mk147 on 2014-03-26
**ok i can reboot into 3.5.0-24 :)**  but i can not connect to the internet by wifi or ethernet so..

---

### Post by Iowan on 2014-03-26
Split to separate thread.

---

### Post by Mk147 on 2014-03-26
where is it ? or we need to create a new thread

---

### Post by Iowan on 2014-03-26
> **Mk147 said:**
> where is it ? or we need to create a new threadYour contributions to a four-year-old thread were moved to a separate thread so your problems can be center stage. An additional benefit - you can mark it [SOLVED] when you get done. :)
THIS is that new thread (notice only 17 posts - instead of ~57)

---

### Post by Mk147 on 2014-03-26
**ahh ok i am really sorry, but this my first time ever posted sth on the internet **:smile: thank you admin

---

### Post by chili555 on 2014-03-27
> **Mk147 said:**
> **ok i can reboot into 3.5.0-24 :)**  but i can not connect to the internet by wifi or ethernet so..Perhaps your ethernet driver didn't load. Let's see what device it is, load it and proceed:```
lspci -nn | grep 0200
```

---

