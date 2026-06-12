---
title: "Asus Rampage IV Black edition wireless driver not working."
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by codepandit on 2016-01-30
Hi everyone, I'm new to ubuntu I have installed ubuntu on my computer everything seems to work fine but wifi. I was wondering if anyone know how can I install wifi drivers for asus rampage IV black edition? [COLOR=#111111][FONT=Ubuntu] I ran this command in terminal lspci -vvnn | grep 14e4, it gave me the chipset of my wifi :** Broadcom Corporation BCM4352 802.11ac wireless network Adapter [14e4:43b1] (rev 03)**. Any idea how can I get the driver from here?[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] [/FONT][/COLOR]Thanks

---

### Post by praseodym on 2016-01-30
Hi,

install the newest Braodcom STA driver via:

```
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb 
```
Reboot.

---

### Post by codepandit on 2016-01-30
> **praseodym said:**
> Hi,

install the newest Braodcom STA driver via:

```
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb 
```
Reboot.

Hi thanks for suggestion, I tried but it gave an error.

[IMG]http://imgur.com/BtqK4oj[/IMG]

---

### Post by praseodym on 2016-01-31
Install first:
```

sudo apt-get install dkms
```Then try it again

---

