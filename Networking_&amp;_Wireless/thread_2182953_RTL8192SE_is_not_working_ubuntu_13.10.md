---
title: "RTL8192SE is not working ubuntu 13.10"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by juandescals on 2013-10-23
Hello,

After upgrading tu 13.10 (from 13.04) my wifi card Realtek RTL8192SE is not working. It seems that it doesn't exit since this message is shwon at the start:

31.073115] rtl8192se: Firmware rtlwifi/rtl8192sefw.bin not available

---

### Post by varunendra on 2013-10-25
> **juandescals said:**
> 31.073115] rtl8192se: Firmware rtlwifi/rtl8192sefw.bin not available
I haven't downloaded 13.10 yet, but that firmware should have been part of the default installation. So it being missing makes me suspicious of a broken installation.

If the rest of the system is working fine, try installing the default firmware package (while connected to internet via cable or modem etc.) -
```
sudo apt-get install linux-firmware
```

If you don't have a working internet connection available, I have attached the firmware file from my installation (12.04.1). Download it to your desktop, then extract to your /lib/firmware/rtlwifi directory -
```
sudo mkdir -p /lib/firmware/rtlwifi
sudo unzip Desktop/rtl8192sefw.bin.zip -d /lib/firmware/rtlwifi
```
The first command will create the "rtlwifi" directory if it does not already exist, won't do anything if it does already exist. The second one will extract the included firmware file to the directory.

After this, do -
```
sudo modprobe -rv rtl8192se
sudo modprobe -v rtl8192se
```
..or simply reboot.

If still having problems, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by juandescals on 2013-11-06
Thank you very much

---

### Post by varunendra on 2013-11-06
You're welcome ! Glad to see you are still with us! :)

---

