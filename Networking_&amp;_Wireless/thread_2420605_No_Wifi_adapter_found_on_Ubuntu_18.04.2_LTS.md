---
title: "No Wifi adapter found on Ubuntu 18.04.2 LTS"
date: 2019-06-07
forum: Networking &amp; Wireless
---

### Post by mary-z on 2019-06-07
Hi everyone!


I recently installed Ubuntu 18.04.2 LTS on HP 17-ca0114ur laptop. I can't connect to Wi-Fi, it says that 'No Wi-Fi Adapter Found'. **Wired connection isn't working too.** I have Win10 on this PC, there were also problems with Wi-Fi in windows, I had to download drivers. 

*wireless-info* script result: [https://paste.ubuntu.com/p/cSp4R4XzRp/](https://paste.ubuntu.com/p/cSp4R4XzRp/)

---

### Post by jeremy31 on 2019-06-07
First reboot and go into UEFI/BIOS settings and disable secure boot, leave the secure boot keys alone, then
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Reboot

---

### Post by mary-z on 2019-06-08
Hi Jeremy! Thanks for your answer.

I disabled secure boot, still no wi-fi connection, so I can't do the second part of your instruction.

---

### Post by jeremy31 on 2019-06-08
Can you connect the computer using USB tethering to a smartphone or connect ethernet to get a connection so you can run the commands to install and build the driver?

---

### Post by mary-z on 2019-06-10
Ethernet isn't working. I followed [this]("https://askubuntu.com/questions/1039233/no-wired-connection-wired-unmanaged-ubuntu-18-04/1043244#1043244") instruction since I had *managed *set to *false *too, but it didn't help. I tried to install packages manually, but each package comes with dependency that comes with dependency... Is there any simpler way to install packages without Internet connection?

---

