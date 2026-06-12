---
title: "WIFI not being recognized in UBUNTU 18.04"
date: 2018-12-09
forum: Networking &amp; Wireless
---

### Post by Muhammad_GUl_ZAin_ on 2018-12-09
[http://paste.ubuntu.com/p/ZkJtXSxwcX/](http://paste.ubuntu.com/p/ZkJtXSxwcX/) In the link you can find all the information regarding my wifi being shown in ubuntu 18.04. I am using Lenovo Y520.

Please help, i am stuck with this problem from months now. I have tried almost every solution out there and most of them link with broadcom problems.

---

### Post by jeremy31 on 2018-12-09
Do ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Reboot

Or you could do a test on a patch I did
```
cd /lib/modules/4.15.0-42-generic/kernel/drivers/platform/x86/
sudo mv ideapad-laptop.ko ideapad-laptop.ko.bak
sudo wget https://www.dropbox.com/s/nxu7b0lyj02bv4n/ideapad-laptop.ko
```
Reboot

---

### Post by praseodym on 2018-12-09
Additionally, blacklist the Broadcom driver(s)
```

echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by abhishek.sethi0202 on 2018-12-12
No wifi adapter found is popped up when i try to open the wifi category in settings in ubuntu 18.04. i am new to linux and have an hp laptop. i have tried many solutions but none worked.
This is an output of sudo lshw -short

OUTPUT:

 sudo lshw -short sudo lshw -short
H/W path       Device       Class          Description
======================================================
                            system         HP Laptop 15-bs0xx (3KM92PA#ACJ)
/0                          bus            832A
/0/0                        memory         128KiB BIOS
/0/4                        processor      Intel(R) Core(TM) i3-7130U CPU @ 2.70
/0/4/5                      memory         128KiB L1 cache
/0/4/6                      memory         512KiB L2 cache
/0/4/7                      memory         3MiB L3 cache
/0/26                       memory         4GiB System Memory
/0/26/0                     memory         4GiB SODIMM DDR4 Synchronous Unbuffer
/0/26/1                     memory         SODIMM DDR Synchronous [empty]
/0/100                      bridge         Intel Corporation
/0/100/2                    display        Intel Corporation
/0/100/4                    generic        Skylake Processor Thermal Subsystem
/0/100/8                    generic        Skylake Gaussian Mixture Model
/0/100/14                   bus            Sunrise Point-LP USB 3.0 xHCI Control
/0/100/14.2                 generic        Sunrise Point-LP Thermal subsystem
/0/100/16                   communication  Sunrise Point-LP CSME HECI #1
/0/100/17                   storage        Sunrise Point-LP SATA Controller [AHC
/0/100/1c                   bridge         Sunrise Point-LP PCI Express Root Por
/0/100/1c/0    eno1         network        RTL8111/8168/8411 PCI Express Gigabit
/0/100/1c.5                 bridge         Sunrise Point-LP PCI Express Root Por
/0/100/1c.5/0               network        Realtek Semiconductor Co., Ltd.
/0/100/1f                   bridge         Intel Corporation
/0/100/1f.2                 memory         Memory controller
/0/100/1f.3                 multimedia     Intel Corporation
/0/100/1f.4                 bus            Sunrise Point-LP SMBus
/0/1           scsi0        storage        
/0/1/0.0.0     /dev/sda     disk           1TB WDC WD10JPVX-60J
/0/1/0.0.0/1                volume         259MiB Windows FAT volume
/0/1/0.0.0/2   /dev/sda2    volume         15MiB reserved partition
/0/1/0.0.0/3   /dev/sda3    volume         244GiB Windows NTFS volume
/0/1/0.0.0/4   /dev/sda4    volume         348GiB Windows NTFS volume
/0/1/0.0.0/5   /dev/sda5    volume         244GiB Windows NTFS volume
/0/1/0.0.0/6   /dev/sda6    volume         979MiB Windows NTFS volume
/0/1/0.0.0/7   /dev/sda7    volume         14GiB Windows NTFS volume
/0/1/0.0.0/8   /dev/sda8    volume         78GiB EXT4 volume
/0/2           scsi1        storage        
/0/2/0.0.0     /dev/cdrom   disk           DVDRW  DA8AESH
/1                          power          JC04041
/2                          power          OEM Define 5
/3             enp0s20f0u1  network        Ethernet interface


Please help so that i can find my way out of it.

---

### Post by chili555 on 2018-12-12
> **abhishek.sethi0202 said:**
> No wifi adapter found is popped up when i try to open the wifi category in settings in ubuntu 18.04. i am new to linux and have an hp laptop. i have tried many solutions but none worked.
This is an output of sudo lshw -short

<snip>
/0/100/1c.5/0               network        Realtek Semiconductor Co., Ltd.
<snip>

Please help so that i can find my way out of it.Rather than tack on to the end of another thread, please start your own new question. Please include the wireless diagnostics from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

