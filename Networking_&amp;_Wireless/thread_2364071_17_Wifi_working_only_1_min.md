---
title: "17 Wifi working only 1 min"
date: 2017-06-18
forum: Networking &amp; Wireless
---

### Post by paolol on 2017-06-18
Hi, just installed a fresh Ubuntu 17 on my MSI GS73 and I found that the Wifi only work for 1 min then I lose the ability to browse the network.
ifconfig show the card connected with ip/netmask all set correctly, but I cant any ip on my sub net same for the internet.
The card is a Killer e2500 .
Any one have found a fix for this ?
Thanks

---

### Post by jeremy31 on 2017-06-18
Please see the wireless script link in my signature and post the results.

---

### Post by paolol on 2017-06-18
Hi thanks,
you can find the script at
[http://paste.ubuntu.com/24891953/](http://paste.ubuntu.com/24891953/)

Thanks

---

### Post by praseodym on 2017-06-18
Try updating the firmware:

```
sudo rm -r /lib/firmware/ath10k
wget http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164.1_all.deb
sudo dpkg -i linux-firmware_1.164.1_all.deb
sudo modprobe -rfv ath10k_pci
sudo modprobe -v ath10k_pci
```

---

### Post by jeremy31 on 2017-06-18
First I would disable wifi power management with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

Set your country code with
```

sudo iw reg set IT
sudo sed -i 's/^REG.*=$/&IT/' /etc/default/crda

```

Reboot

---

### Post by paolol on 2017-06-18
Thanks to both of you, disabling the wifi power management solve the problem when the pover supply was connected, but wifi was not working when the power supply was disconnected.
So I installed the new driver and now all works  perfectly.
thanks again

---

