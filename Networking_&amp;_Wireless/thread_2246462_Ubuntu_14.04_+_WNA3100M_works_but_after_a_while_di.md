---
title: "Ubuntu 14.04 + WNA3100M: works but after a while dies."
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by MasterMaxus on 2014-09-30
Hi People,

I have setup and configured a WNA3100M using the various posts I have found on this forum.

The device works okay for small things, but when copying large files with rsync it dies and kills the network connection (I cant ping anything from the machine once this happens). If i do ifdown and ifup the device comes back to life and works correct until i rsync again.

I'm using the ndiswrapper and the driver I found on this forum called: 2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz

I'm currently using the 64 bit driver from that package.

I haven't been able to find any information or errors relating to the drop out, any ideas where to look or what I should try?

Also I've attached my wireless info.

Thanks!

---

### Post by Vladlenin5000 on 2014-10-01
Honestly, my only suggestion is getter a better device, natively supported. You can find many for less than US$10. C'mon...

---

### Post by varunendra on 2014-10-01
Your adapter seems to be natively supported by the rtl8192cu driver, why have you installed ndiswrapper?

To start troubleshooting, please purge it first -
```
sudo modprobe -rv ndiswrapper
sudo apt-get purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper
sudo sed -i '/ndiswrapper/ d' /etc/modules
```

Then see if the native driver works any better. If not, please try a patched driver suggested here : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)
..and if the problem persists, please post a fresh wireless_script report after doing above.

---

### Post by QIII on 2014-10-01
*Moved to **Networking & Wireless***

---

