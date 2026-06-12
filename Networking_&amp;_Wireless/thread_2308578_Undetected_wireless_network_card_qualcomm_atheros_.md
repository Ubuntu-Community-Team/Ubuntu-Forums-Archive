---
title: "Undetected wireless network card qualcomm atheros qca61x4"
date: 2016-01-04
forum: Networking &amp; Wireless
---

### Post by yvind3 on 2016-01-04
Internet access only with cable. Works with external wireless network card, but not with the internal that works in windows (dual-booting).
The wireless network card is qualcomm atheros qca61x4. I'm running Ubuntu 14.04.3 LTS

OUTPUT (**lspci -knn | grep Net -A2**):
```
07:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 20)
    Subsystem: Lite-On Communications Inc Device [11ad:0804]
    Kernel driver in use: ath10k_pci
```

OUTPUT (**rfkill list**):
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

(The last code should contain info about the wireless card too (?))

How can I activate the network card (I'm new to ubuntu)?

UPDATE:

OUTPUT (**sudo modprobe ath10k_pci && dmesg | grep ath**):
```
[   12.204567] ath10k_pci 0000:07:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   13.143199] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2
[   13.143239] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:003e:11ad:0804.bin failed with error -2
[   13.143241] ath10k_pci 0000:07:00.0: failed to load spec board file, falling back to generic: -2
[   13.143245] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board.bin failed with error -2
[   13.143247] ath10k_pci 0000:07:00.0: failed to fetch generic board data: -2
[   13.143248] ath10k_pci 0000:07:00.0: failed to fetch board file: -2
[   13.143249] ath10k_pci 0000:07:00.0: could not fetch firmware files (-2)
[   13.143251] ath10k_pci 0000:07:00.0: could not probe fw (-2)
```

---

### Post by chili555 on 2016-01-04
Do the message logs suggest that you are missing firmware that we may be able to find and install?```
sudo modprobe ath10k_pci && dmesg | grep ath
```

---

### Post by yvind3 on 2016-01-04
Updatet the question with the result. Not entirely sure how to interpret it...

---

### Post by chili555 on 2016-01-04
As we suspected, you are missing the required firmware. With a working internet connection by ethernet, tethered or whatever means possible, please open a terminal and do:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/QCA6174/*   /lib/firmware/ath10k
sudo mv /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1
 /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin
```Reboot.

---

### Post by yvind3 on 2016-01-04
Command #4 gave no output, and command #5 gave following:
```
mv: cannot stat &#8216;/lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1&#8217;: No such file or directory
```
Tried rebooting anyway -- no effect. I'm wondering if it's because of the lineshift in #5, which I interpreted as just space..?

---

### Post by jeremy31 on 2016-01-04
Try ```
sudo rm -r /lib/firmware/ath10k
sudo cp -r ath10k-firmware/ /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin
```

---

### Post by yvind3 on 2016-01-04
Performed the commands and rebooted -- everything works as it should now! Thanks for all the help :)

---

### Post by chili555 on 2016-01-04
Glad it's working and thanks @jeremy31!

---

### Post by edmon1 on 2016-10-29
hi 
am newbie 
i have this problm 
and i downladed the ath10k from github
and put it manually in lib/firmware/ath10k
aftr restart but my wifi doesnt work in kali plz help if i have mistak!!

---

