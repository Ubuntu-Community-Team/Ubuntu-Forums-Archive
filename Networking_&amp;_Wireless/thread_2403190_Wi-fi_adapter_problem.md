---
title: "Wi-fi adapter problem"
date: 2018-10-08
forum: Networking &amp; Wireless
---

### Post by hyperion101010 on 2018-10-08
i am having the same problem and sadly it isnt working for me 
sudo modprobe -v rtl8723de
insmod /lib/modules/4.15.0-34-generic/kernel/drivers/net/wireless/realtek/rtlwifi/phydm/phydm_mod.ko 
modprobe: ERROR: could not insert 'rtl8723de': Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by praseodym on 2018-10-08
Check
```

dmesg | grep rtl
```

---

### Post by hyperion101010 on 2018-10-08
i have an error
cleaning build area.....(bad exit status: 2)
make -j4 KERNELRELEASE=4.15.0-34-generic -C /lib/modules/4.15.0-34-generic/build M=/var/lib/dkms/rtlwifi-new/0.6/build....

---

### Post by hyperion101010 on 2018-10-08
this happened while doing dkms install rtlwifi_new/0.6

---

### Post by coffeecat on 2018-10-08
@hyperion101010, I have moved the posts you made in two others threads, both marked solved, together with the one reply you have received, into your own thread.

Please do not hijack other people's threads, but start your own. Since the threads you posted to were about different model laptops, I suggest you describe your own hardware.

---

### Post by hyperion101010 on 2018-10-08
this came
[   19.347273] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=826c lmp_ver=08 lmp_subver=8873
[   19.347275] Bluetooth: hci0: rtl: assuming no firmware upload needed
[   19.719140] rtlwifi: loading out-of-tree module taints kernel.
[   19.719209] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   20.047273] rtl8723de: Using firmware rtlwifi/rtl8723defw.bin
[   20.121148] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.121352] rtlwifi: rtlwifi: wireless switch is on
[   20.122651] rtl8723de 0000:03:00.0 wlo1: renamed from wlan0

---

### Post by hyperion101010 on 2018-10-08
oh solved it thanks maybe new rtlwifi_new is the fix for it

---

