---
title: "ubuntu 17.10 - no wi-fi adapter found"
date: 2017-10-28
forum: Networking &amp; Wireless
---

### Post by waloszczyk on 2017-10-28
Hi, im totaly beginer of ubuntu. i have 17.10 vers. and this is my first Ubuntu.
Generaly almost all works. I have problem with wi-fi.
i have info that "no wifi adapter found". Additional driver are ok (i think so) but wifi still not works.
could sb help?

ps. notbook HP-255-G4

---

### Post by jeremy31 on 2017-10-28
Is Secure Boot disabled in BIOS?  Check
```
lspci -nnk | grep -iA3 net
```
Look for "Kernel module in use" for the wifi

---

### Post by waloszczyk on 2017-10-28
Secure boot in bios:"system configuration" is ENABLED now.

---

### Post by jeremy31 on 2017-10-28
Secure Boot needs to be disabled or the driver can't load because of Secure Boot enforcement in the kernel

---

### Post by waloszczyk on 2017-10-28
YES YES YES.........thxs a lot!!!!!!!!!!!!! :)

---

### Post by praseodym on 2017-12-17
You need this firmware

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by yak613 on 2018-04-02
This didn't work for me. I a) went into BIOS and turned off Secure boot, and installed the firmware, rebooted, still no luck.

---

### Post by wildmanne39 on 2018-04-02
Hello and welcome to the forum yak613, please start your own thread in the networking section of the forum and post the results of the wireless script in my signature and someone will help you.

Thanks

---

### Post by younixforme on 2018-07-02
> **jeremy31 said:**
> Is Secure Boot disabled in BIOS?  Check
```
lspci -nnk | grep -iA3 net
```
Look for "Kernel module in use" for the wifi

Worked for me. Using Ubuntu 18.04 LTS on an HP Pavilion dv6000.  Thank you!

---

