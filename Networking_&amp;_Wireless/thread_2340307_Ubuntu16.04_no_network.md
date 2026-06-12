---
title: "Ubuntu16.04 no network"
date: 2016-10-17
forum: Networking &amp; Wireless
---

### Post by ganl-140593 on 2016-10-17
Hello,

I just installed the ubuntu 16.04 on my machine but without network. 
I tried to reinstall the Realtek PCI GBE Family Controllers r8168/r8169 drivers(both separately) but failed both.
Here is the screenshot when I make install the r8169 driver.

```
sudo make install
make -C /lib/modules/4.4.0-21-generic/build  SUDIRS=/home/louisegan/r8159-6.022.00/src INSTALL_MOD_DIR=kernel/drivers/net/ethernet/realtek modules_install
make[1]:Entering directory 'usr/src/linux-headers-4.4.0-21-generic'
INSTALL /home/louisegan/r8169-6.022.00/src/r8169.ko
At main.c:222:
SSL error: 02001002:system library:fopen:No such file or directory: bss_file.c:175
SSL error: 2006D080:BIO routines: BIO_new_file:no such file: bss_file.c:178:sign-file:certs/signing_key.pem: No such file or directory
DEPMOD 4.4.0-21-generic
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-21-generic'

```

Here is the screenshot when I tried to install r8168 driver.
```
cd ./r8168-8.040.00/
sudo ./autorun.sh

Check old driver and unload it.
rmmod r8169
Build the module and install
make[2]: *** No rule to make target 'kernel/drivers/net/wireless/realtek' 
make[1]: *** [install] Error 2
make: [install] Error 2
```

Can anyone figure this out for me? I cannot access any network from ubuntu for now.

---

### Post by chili555 on 2016-10-17
> sudo make install
make -C /lib/modules/4.4.0-21-generic/build  SUDIRS=/home/louisegan/r8159-6.022.00/src INSTALL_MOD_DIR=kernel/drivers/net/ethernet/realtek modules_install
make[1]:Entering directory 'usr/src/linux-headers-4.4.0-21-generic'
INSTALL /home/louisegan/r8169-6.022.00/src/r8169.ko
At main.c:222:
SSL error: 02001002:system library:fopen:No such file or directory: bss_file.c:175
SSL error: 2006D080:BIO routines: BIO_new_file:no such file: bss_file.c:178:sign-file:certs/signing_key.pem: No such file or directory
DEPMOD 4.4.0-21-generic
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-21-generic'
This doesn't look like an error to me; the module built. Did you reboot? Is the behavior improved?

May we see:```
ifconfig
dmesg | grep enp
```

---

### Post by praseodym on 2016-10-17
Driver version "40" is too old. Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.042.00-2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.042.00-2_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11.2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11.2_all.deb)

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by ganl-140593 on 2016-10-17
Thank you, this solved my problem. Finally I can access the network.
But I have another problem here, that is the network is rather unstable abnormally (this moment it can open a web page; a few minutes later, the page alerts cannot find the host server). Since I've got double OS systems, I can guarantee that it's not a problem of network itself because under the other OS, everything works just fine.

---

### Post by ganl-140593 on 2016-10-17
I rebooted for several times. But failed. The other answer to installer a newer driver solved my problem.

---

