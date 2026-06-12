---
title: "Wireless failure after update"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by musical1too on 2008-06-05
I was able to get my wireless networking after compiling a module for my Atheros 5007 that was available from the madwifi organization and the article is at [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html). This was with kernel 2.6.24-16. When the kernel updated to 2.6.24-17 the wireless card disappeared, so I went to the madwifi-ng-r2756+ar5007 directory and again typed make and sudo make install. Once again the Atheros wireless card appeared and worked fine. Now with the update to kernel 2.6.24-18 i attempted the same procedure, but nothing will get my atheros wireless card to appear. Booting into previous kernels does not help as the Knetwork manager says there is no wireless device present. I'm not sure what to check to get my wireless working.

---

### Post by chili555 on 2008-06-05
Please try:```
cd madwifi-ng-r2756+ar5007
**make clean**
make
sudo make install
```Let us know.

---

### Post by musical1too on 2008-06-05
Thank you for your prompt response.
I went to the madwifi-ng-r2756+ar5007 directory and typed
make clean
make
sudo make install

and an iwlist scan shows no interface that supports scanning. Thank you for the suggestion, but I don't know where to look next.

---

### Post by musical1too on 2008-06-05
I completely forgot to mention that I am running Kubuntu 8.04 on a HP Pavilion dv9815nr laptop.

---

### Post by chili555 on 2008-06-05
After you originally did the compile and install, did you *sudo modprobe ath_pci* or some other modprobes to get the newly compiled module loaded? Did you do so this time?

---

### Post by musical1too on 2008-06-05
After you originally did the compile and install, did you sudo modprobe ath_pci or some other modprobes to get the newly compiled module loaded? Did you do so this time?

No. The first two times I compiled the module wireless always worked immediately. As you suggested, I did 
sudo modprobe ath_pci
and within 15 seconds I was prompted by kdewallet for the password to get connected.

Thank you very much for your experience and insight.

At this point will i need to modprobe ath_pci after every boot?

---

### Post by chili555 on 2008-06-05
It *should* load automatically; the only way to be sure is to reboot! If it does not load, that is, you have no wireless, modprobe it again. Then *sudo gedit /etc/modules* and add:```
ath_pci
```Save and close gedit and you should be all set.

---

### Post by calcfreak83 on 2008-06-06
I'm Getting the same thing. I recently updated to the latest kernel (2.6.24-18-generic), and now, wireless is dead. 
/etc/modules has ath-pci

`lsmod | grep ath` returns 
```

ath_rate_sample        15232  1
ath_pci               113448  0
wlan                  211760  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280416  3 ath_rate_sample,ath_pci

```

but iwlist scan returns
...
```

ath0      No scan results

```
I am currently using the 2756 version of the driver.

---

### Post by chili555 on 2008-06-07
From *man iwlist*:>  Triggering  scanning  is  a privileged operation (root only) and normal users can only read left-over scan results.  By  default, the way scanning is done (the scope of the scan) is dependant on the card and card settings.So you will likely get a better result with:```
**sudo** iwlist ath0 scan
```

---

