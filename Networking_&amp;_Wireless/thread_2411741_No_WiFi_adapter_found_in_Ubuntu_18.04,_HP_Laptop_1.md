---
title: "No WiFi adapter found in Ubuntu 18.04, HP Laptop 14-CMxxxxxx"
date: 2019-02-03
forum: Networking &amp; Wireless
---

### Post by richoandika on 2019-02-03
I've installed my Ubuntu 18.04, but why i cant use wifi? "No Wi-Fi Adapter Found
Attaching pastebin link from terminal outputs.

[https://paste.ubuntu.com/p/bXJQy4mHyP/](https://paste.ubuntu.com/p/bXJQy4mHyP/)

---

### Post by jeremy31 on 2019-02-03
First reboot and go into BIOS settings and disable Secure Boot, do not delete the keys, then in terminal do
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Reboot

---

### Post by richoandika on 2019-02-03
Still not found broo

---

### Post by richoandika on 2019-02-03
Still not found

---

### Post by jeremy31 on 2019-02-03
Run wireless script again and post new results

---

### Post by richoandika on 2019-02-03
how? i dont know please helpme

---

### Post by jeremy31 on 2019-02-03
In terminal do ```
./wireless-info
cat wireless-info.txt | nc termbin.com 9999
```
Post termbin URL from terminal

---

### Post by richoandika on 2019-02-03
[https://paste.ubuntu.com/p/Kpdgw8VP6S/](https://paste.ubuntu.com/p/Kpdgw8VP6S/)

---

### Post by richoandika on 2019-02-03
and my bluetooth like that too, not found

---

### Post by jeremy31 on 2019-02-03
Secure Boot is still enabled in BIOS/UEFI, the driver can't be loaded until it is disabled, try
```
sudo modprobe -v rtl8723de
```
You will see that the kernel will not load it as it isn't signed

---

### Post by richoandika on 2019-02-03
richoandika@hp:~$ sudo modprobe -v rtl8723de
insmod /lib/modules/4.15.0-45-generic/updates/dkms/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8723de': Required key not available

---

### Post by richoandika on 2019-02-03
richoandika@hp:~$ sudo modprobe -v rtl8723de
insmod /lib/modules/4.15.0-45-generic/updates/dkms/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8723de': Required key not available

---

### Post by jeremy31 on 2019-02-03
Disable Secure Boot and that problem vanishes

---

### Post by richoandika on 2019-02-03
Thanks the wifi problem solved but my bluetooth is not, hot to fix it?

---

### Post by jeremy31 on 2019-02-03
We can try fixing the bluetooth with
```
cd
git clone https://github.com/jeremyb31/newbtfix-4.15.git
sudo dkms add ./newbtfix-4.15
sudo dkms install btusb/4.0
cd /lib/firmware/rtl_bt
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/rtl_bt/rtl8723d_config.bin
```
Reboot

---

### Post by richoandika on 2019-02-03
Stuck at loading
[http://prntscr.com/mg0qy2](http://prntscr.com/mg0qy2)

---

### Post by jeremy31 on 2019-02-03
Post results from terminal for ```
dmesg | egrep -i 'blue|firm'
```

---

### Post by richoandika on 2019-02-03
[https://paste.ubuntu.com/p/pFcX2PGGg6/](https://paste.ubuntu.com/p/pFcX2PGGg6/)

---

### Post by jeremy31 on 2019-02-03
Can you try a 4.18 kernel or Ubuntu 18.10 ISO and see if bluetooth works

---

### Post by richoandika on 2019-02-03
Big thanks its solved maybe later i try that version

---

