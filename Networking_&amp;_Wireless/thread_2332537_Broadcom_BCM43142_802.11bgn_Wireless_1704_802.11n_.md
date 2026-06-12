---
title: "Broadcom BCM43142 802.11b/g/n Wireless 1704 802.11n + BT 4.0"
date: 2016-08-01
forum: Networking &amp; Wireless
---

### Post by doodlez on 2016-08-01
Hi! 
I cannot see any WiFi network above 11 chance under Ubuntu 16.04.1. I have tried to change region but nothing has changed. By default system uses proprietary Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source.
Under Windows it does see 1-13 channels with no issue.

---

### Post by zeronoid on 2016-08-01
I have also a problem with the same wifi cart , use this script to get info about your wifi interface when you are using wifi only , close other connection ( wire ..) [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info) This gonna help other people to help you

---

### Post by praseodym on 2016-08-01
Depends on the country code settings, also maybe the driver is not up to date?!
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb 
```
Country code:

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=[COLOR="#FF0000"]DE[/COLOR]/g" /etc/default/crda 
```
Change "DE" for Germany to your one and reboot:

[https://en.wikipedia.org/wiki/ISO_3166-1](https://en.wikipedia.org/wiki/ISO_3166-1)

Check

```
iwlist chan
```

afterwards

---

### Post by doodlez on 2016-08-01
> **praseodym said:**
> Depends on the country code settings, also maybe the driver is not up to date?!
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb 
```
Country code:

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=[COLOR=#FF0000]DE[/COLOR]/g" /etc/default/crda 
```
Change "DE" for Germany to your one and reboot:

[https://en.wikipedia.org/wiki/ISO_3166-1](https://en.wikipedia.org/wiki/ISO_3166-1)

Check

```
iwlist chan
```

afterwards

nothing has changed... 
anyway it says that 12 and 13 become  available, but it still doesn't see any network. I have manually  switched my router to 11 channel. 
> dell@dell:~$ iwlist chan
enp7s0    no frequency information.

lo        no frequency information.

wlp6s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
 

Here is log for **zeronoid**

---

### Post by praseodym on 2016-08-01
Change the encryption mode to pure WPA2-AES (CCMP), not mixed mode WPA/WPA2. If you are using such networks frequently, I strongly recommend using Wicd:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
You can chose mixed mode there, too. If it works you can uninstall the network manager or remove it from autostart

---

### Post by praseodym on 2016-08-01
```
[   11.692934] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.695450] wl: module verification failed: signature and/or required key missing - tainting kernel
```
This error message occurs if secure boot is activated! Try disabling it first!

---

### Post by doodlez on 2016-08-01
**praseodym**, I don't have any issue with encryption, I have an issue with networks which works above 11 channel. And Secure Boot is disabled by default in UEFI.

---

### Post by jeremy31 on 2016-08-01
I think this is a restriction in most broadcom kernel modules or the firmware used.  I haven't found anything in the bcmwl source code but that is a lot of code but I have found references to restricted 2.4Ghz in b43 and brcmsmac source code

---

### Post by doodlez on 2016-08-01
> **jeremy31 said:**
> I think this is a restriction in most broadcom kernel modules or the firmware used.  I haven't found anything in the bcmwl source code but that is a lot of code but I have found references to restricted 2.4Ghz in b43 and brcmsmac source code
it looks like restriction for me now. I haven't found any solution for linux...

---

