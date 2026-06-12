---
title: "Broadcom BCM4352 Randomly disconnects and reconnects 16.10"
date: 2017-01-11
forum: Networking &amp; Wireless
---

### Post by edward-molyneux4-l on 2017-01-11
I have a HP Envy laptop dual booting Ubuntu and Windows 10. It has the following wireless card:

08:00.0 Network controller [0280]: Broadcom Limited BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)

I use this laptop at work, when I start up the laptop the Network Manager symbol shows the Wi-Fi symbol, but at some point, the Wi-Fi will disconnect and the Wi-Fi symbol will be replaced with the two arrows that indicate an ethernet connection. The internet will reconnect, but it will not change the symbol back to the Wi-Fi and remain with the Ethernet symbol.

When I click the Network Manager icon it says that the "Wi-Fi Network" is "Device not ready." The internet will then disconnect and reconnect throughout the day at random intervals. It also gets very slow at other times - something my colleagues don't experience. 

I've tried the solution found here: [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers) And although that seemed to work initially, it didn't change anything. Also, the button on my laptop (F12) that turns the Wireless off also doesn't work, if I push it, it disables the Wi-Fi, but then will not reenable it without a reboot.

As a side note, the wireless works flawlessly on Windows 10 and I've never had any issues.

Many thanks for any help you can give me.

---

### Post by praseodym on 2017-01-13
Please run the wireless script from the sticky thread and show the outputs

---

### Post by edward-molyneux4-l on 2017-01-16
Apologies I missed that. Please find attached.

---

### Post by praseodym on 2017-01-16
Which driver version is installed?
```

dpkg -l broadcom-* | grep ii
dpkg -l bcmwl-* | grep ii
```
Please check deactivating secure boot in your BIOS/UEFI

---

### Post by edward-molyneux4-l on 2017-01-17
```

edward@edward-HP-ENVY-15-Notebook-PC:~$ dpkg -l broadcom-* | grep ii
dpkg-query: no packages found matching broadcom-*
edward@edward-HP-ENVY-15-Notebook-PC:~$ dpkg -l bcmwl-* | grep ii
ii bcmwl-kernel-source 6.30.223.248+bdcom-0ubuntu11 amd64 Broadcom 802.11 Linux STA wireless driver source

```

Secure boot is disabled as I had to do that to make Grub display, I also cleared the "secure boot" flags in my BIOS.

---

### Post by praseodym on 2017-01-17
Driver 248 is too old and buggy:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
Install this one instead:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-4_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-4_all.deb
```

---

### Post by edward-molyneux4-l on 2017-01-18
I've updated the drivers, I'll post back if the disconnecting continues. But the Wi-Fi button the keyboard is still not functioning as it should be.

---

### Post by edward-molyneux4-l on 2017-01-18
Unfortunately updating the drivers hasn't worked, it's still DCing.

---

### Post by edward-molyneux4-l on 2017-01-30
Bump

---

### Post by geeksmith on 2017-01-30
Do you have administrative control of the wireless point that services the "PLMR" SSID you're using? If so, you need to get off channel 3. In 2.4GHz, channels 1, 6, and 11 provide the best separation from other access points, and thus a better signal quality. The way it stands, you're both inducing and receiving significant interference from all access points below channel 9.

If you switch to channel 1, 6, or 11 you'll have less interference, but there are access points on all three of those channels. A better solution would be switching to a 5GHz channel.

---

### Post by praseodym on 2017-01-30
Meanwhile driver version 5 is out:
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://ubuntu-master.mirror.tudos.de/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-5_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-5_all.deb 
```

---

### Post by edward-molyneux4-l on 2017-01-31
> **geeksmith said:**
> Do you have administrative control of the wireless point that services the "PLMR" SSID you're using? If so, you need to get off channel 3. In 2.4GHz, channels 1, 6, and 11 provide the best separation from other access points, and thus a better signal quality. The way it stands, you're both inducing and receiving significant interference from all access points below channel 9.

If you switch to channel 1, 6, or 11 you'll have less interference, but there are access points on all three of those channels. A better solution would be switching to a 5GHz channel.

Unfourntately I don't frustratingly.

---

### Post by edward-molyneux4-l on 2017-01-31
I've updated the drivers as suggested but Wi-Fi is still disconnecting.

---

