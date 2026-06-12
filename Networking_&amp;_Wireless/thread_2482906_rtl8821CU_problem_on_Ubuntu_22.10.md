---
title: "rtl8821CU problem on Ubuntu 22.10"
date: 2023-01-13
forum: Networking &amp; Wireless
---

### Post by bmc on 2023-01-13
Good evening.

I have a WiFi + Bluetooth USB adapter. With Ubuntu 22.04 it worked perfectly. Upgrading to 22.10 it has stopped working.

The output of the lsusb command is:
Bus 002 Device 003: ID 0bda:c820 Realtek Semiconductor Corp. 802.11ac NIC

I am trying to reinstall the driver with dkms but I get an error:

~/rtl8821CU$ sudo ./dkms-install.sh
About to run the dkms installation steps....
Creating symbolic link /var/lib/dkms/rtl8821CU/5.4.1/source -> /usr/src/rtl8821CU-5.4.1
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Build module:
Cleaning up compilation area....
make' KVER=5.19.0-29-generic.............................(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8821CU: 5.4.1 not found
ERROR! Bad return status for module build on kernel: 5.19.0-29-generic (x86_64)
See /var/lib/dkms/rtl8821CU/5.4.1/build/make.log for more information.
Sign the command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Build module:
Cleaning up compilation area....
make' KVER=5.19.0-29-generic.........................(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8821CU: 5.4.1 not found
ERROR! Bad return status for module build on kernel: 5.19.0-29-generic (x86_64)
See /var/lib/dkms/rtl8821CU/5.4.1/build/make.log for more information.
Finished running the dkms installation steps.

I would appreciate any help.

Best regards,

---

### Post by chili555 on 2023-01-14
May we see a link to the driver file you downloaded? May we also see:```
sudo dkms status
```

---

### Post by bmc on 2023-01-14
> **chili555 said:**
> May we see a link to the driver file you downloaded? May we also see:```
sudo dkms status
```

$ sudo dkms status
rtl8821CU/5.4.1: added

Download it from here:

[https://github.com/brektrou/rtl8821CU](https://github.com/brektrou/rtl8821CU)

Best regards

---

### Post by chili555 on 2023-01-14
> make' KVER=[COLOR="#FF0000"]5.19.0-29-generic[/COLOR]..The 5.4.1 branch at the repository says, clearly: > brektrou Support Linux up to version 5.5.xI am quite confident that it will not compile without error on 5.19. I tested the later branch, 5.8.1 as well as the master branch on my 5.19 system and none compile without fatal errors. You will need another package.

I suggest:
```
sudo dkms remove rtl8821CU/5.4.1 --all
git clone https://github.com/morrownr/8821cu-20210118.git
cd 8821cu-20210118
sudo ./install-driver.sh 

```
Reboot.

---

### Post by morrownr on 2023-01-14
From the previous message:

> sudo install-driver.sh

Change the above to:

$ sudo ./install-driver.sh

There are a lot of docs in the repo:

[https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)

This repo is a placeholder that will always give the link to the current driver. The repo shown in the previous message will be depreciated in 2-4 weeks as a new driver will be coming online. The new driver is really good. The current driver works well and is stable but the new driver supports MU-MIMO and many enhancements so you'll probably want to upgrade to it. Good luck.

---

### Post by chili555 on 2023-01-14
> sudo ./install-driver.shmorrownr is quite correct. Sorry for my mis-step.

Thanks, Nick, for your careful eye!

---

### Post by bmc on 2023-01-15
Hello

Thank you all.

Your help was good for me.

It works ok.

Regards

---

### Post by morrownr on 2023-01-16
> **chili555 said:**
> morrownr is quite correct. Sorry for my mis-step.

Thanks, Nick, for your careful eye!

chili555, no problem. I'll never be as good as your are at helping people but I do already in my nitch.

---

### Post by chili555 on 2023-01-16
Removed.

---

### Post by chili555 on 2023-01-16
> **morrownr said:**
> chili555, no problem. I'll never be as good as your are at helping people but I do already in my nitch.I'm quite certain that you've helped millions. Your repo is invaluable.

Thanks so much for your very kind words.

---

