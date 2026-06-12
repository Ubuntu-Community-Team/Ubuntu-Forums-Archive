---
title: "Stuck with a desktop computer with WIFI but no ethernet cable possible"
date: 2020-04-03
forum: Networking &amp; Wireless
---

### Post by datagueule on 2020-04-03
Hi All! 

I really tried my best to do it myself and scroll through post to try to fix the problem but it's been hours and I'm stuck.

So I have an ubuntu 18.04 bionic on HP desktop with Wifi but no possibility to connect an ethernet cable (living in a basement, no access to landlord, they fled the coronavirus) but I have a laptop.
my settings says "no wifi adapter found"

I tried 2 methods :

1) [this one]("https://askubuntu.com/questions/1152159/how-to-enable-wifi-on-ubuntu-server-18-04-without-existing-connection") 
[https://askubuntu.com/questions/1152159/how-to-enable-wifi-on-ubuntu-server-18-04-without-existing-connection](https://askubuntu.com/questions/1152159/how-to-enable-wifi-on-ubuntu-server-18-04-without-existing-connection)

So I wrote first:

```
sudo nano /etc/netplan/*.yaml
```

and wrote this:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0f1:
      addresses: [10.0.0.131/24]
      gateway4: 10.0.0.1
      nameservers
        addresses: [10.0.0.1, 8.8.4.4, 8.8.8.8]
      optional: true
  wifis:
    wlp3s0:
      dhcp4: yes
      access-points:
        "network_ssid_name": TELUS666
          password: "inputMyPasswordBetweenTheseBrackets"
```
NOTE: I didn't change anything else than the 2 last lines with my network name and my password

and I manually downloaded the two packages from my laptop "wireless tools" and "wpas supplicant"
put them on a USB key
and installed them on my desktop with 
```
sudo dpkg -i thepackage.deb
```

then I did what he suggest:
```
sudo netplan --debug generate
``` # make config files

  ```
sudo netplan apply 
```# apply new configuration

  ```
reboot
``` # reboot and verify proper operation

It didn't worked. Still "no wi-fi adapter found".

Then I came here, found this:

2) [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

With the broadcam series WiFi.
So I run first to purge if I had something installed by mistake:
```
sudo apt-get purge bcmwl-kernel-source
```

Then I ran his command to see what type of broadcam. I have this:
```
03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43228 802.11a/b/g/n [*14e4:4359*] 
```

so according to the list I need to get this package: ```
bcmwl-kernel-source
```
went to get the package from[ here]("https://packages.ubuntu.com/bionic/amd64/bcmwl-kernel-source/download")
downloaded the one for 18.04 amd64 (that's my system)
and install on my desktop.

The problem now is that this bcmwl package depend on other packages. like dkms. Which depend on other packages. Etc.
anyway I would like to avoid downloading 100 packages manually, just to get my wi-fi if possible :D 

any ideas how to proceed ? 

thank you!!!

---

### Post by chili555 on 2020-04-03
Do you still have your original Ubuntu install USB or DVD? All the required packages are on it. The general process is outlined here: [https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949](https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949)

---

### Post by datagueule on 2020-04-03
Hi! thanks for your help!
great resources,

but I could not insert 'wl': not permitted. So as you explained I need to disable secure boot, I googled and it says that I need to run this: 
```
sudo mokutil --disable-validation
```

but it says "failed to request new MokSB state".

I have a windows on a second drive (not a partition, a 500 HDD and my ubuntu is on a 500 SSD) does this influence something?

thank you!

---

### Post by datagueule on 2020-04-03
it worked!
did another method from here:
[https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS)

would you advice to enable again the secure boot or we don't care?

thaks for your heeelp

---

### Post by chili555 on 2020-04-04
> **datagueule said:**
> it worked!
did another method from here:
[https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS)

would you advice to enable again the secure boot or we don't care?

thaks for your heeelpIf you followed the steps in the link, you can probably once again enable secure boot in the BIOS/EFI.

I am not sure that it provides all that much protection, but some is better than none.

I am glad your wireless is working.

---

