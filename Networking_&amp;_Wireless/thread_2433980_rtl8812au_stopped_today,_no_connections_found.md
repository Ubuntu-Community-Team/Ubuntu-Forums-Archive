---
title: "rtl8812au stopped today, no connections found"
date: 2019-12-28
forum: Networking &amp; Wireless
---

### Post by cvman-16 on 2019-12-28
[https://pastebin.com/2hESsCvC](https://pastebin.com/2hESsCvC)

I"m still fairly new to Ubuntu, got everything working earlier this month, this morning as I sat to start a stream, I attempted to change networks and the service never reconnected. I found the last post that helped me but have not had any luck.  I can confirm the external USB dongle has lights on it, so is functioning as I would expect.

The Broadcom reference you see isn't the problem that is my work around to get line.

Any assistance would be greatly appreciated.

Brett

---

### Post by jeremy31 on 2019-12-28
I will look at results a bit longer, but if you wish to use the internal wifi card do
```
sudo apt install firmware-b43-installer
```
Reboot and post new script results

---

### Post by cvman-16 on 2019-12-28
[https://pastebin.com/ZQ9fJZHy](https://pastebin.com/ZQ9fJZHy)

Run and updated.

Thanks, no rush, I appreciate it.

Brett

---

### Post by jeremy31 on 2019-12-28
I think you are using rtl8812au-dkms from the repos, lets get rid of it
```
sudo apt remove rtl8812au-dkms
```
Install something that might work better
```
sudo apt install git
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
```
Reboot

---

### Post by cvman-16 on 2019-12-28
Just to be clear, in between the reboot, I am disconnecting my cellphone to see if wi-fi becomes the primary option again. but as always upon attempting to "select my network" no hosts are found.

[https://pastebin.com/wWqL12R5](https://pastebin.com/wWqL12R5)

---

### Post by praseodym on 2019-12-28
> ```
[   28.085479] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2 (repeated 2 times)
[   28.095899] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   28.095942] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.095948] b43-phy1 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   28.095953] b43-phy1 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

Try

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by jeremy31 on 2019-12-28
Anything change after ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by cvman-16 on 2019-12-28
Ran each of the statements independently, then had to drive my son to work. but upon my return, I see Wi-Fi is live again, actually looks a little diferent in the functionality buy it'm online thats the important thing. I can't very well leave my phone tethered to this computer 24/7.

Thank you for all the suggestions!

Brett

---

