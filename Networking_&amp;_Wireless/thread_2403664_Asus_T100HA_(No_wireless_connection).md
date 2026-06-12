---
title: "Asus T100HA (No wireless connection)"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by abhishekroy49 on 2018-10-14
I have an ASUS T100HAN. This product:- 



I need help setting up the network card for this device, step by step. I am new to using Linux.

---

### Post by chili555 on 2018-10-14
Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nnk | grep 0280
dmesg | grep -i sdio
```We suspect the Broadcom needs some firmware.

---

### Post by abhishekroy49 on 2018-10-14
I posted the screenshot after inputting the commands.

---

### Post by chili555 on 2018-10-14
On another computer, go here: [https://github.com/Asus-T100/firmware/blob/master/brcm/brcmfmac43340-sdio.txt](https://github.com/Asus-T100/firmware/blob/master/brcm/brcmfmac43340-sdio.txt)

Copy and paste the entire file from here: ```
#T100TAF_AP6234ANS_NVRAM_V1.4.6_20140819_WIN8.1_WW.txt
# 20140819 V1.4.6_WW
# Update ccode to WW
#
# 20140815 V1.4.6_US
# Update ccode to US
#
# 20140730 V1.4.6
# Power offset adjustment
#
# 20140615 V1.4.4
# Add interference and btc params and sd_gpdc=0 to fix CS issue
#
# 20140504 V1.4
# Initial version
manfid=0x2d0
prodid=0x0653
```All the way down to here:```
sd_gpout=4
sd_gpval=1
sd_gpdc=0
aci_detect_en_2g=1
interference=3
#BTC params
btc_flags=71
btc_params8=15000
btc_params22=8000
btc_params83=20000
btc_params84=10000
```After you have all 145 lines copied, save it and name it brcmfmac43340-sdio.txt.

Note: there appears to be a little box or some other symbol at the very beginning, like this: #T100TAF_AP6234ANS_NVRAM_V1.4.6_20140819_WIN8.1_WW.txt

Please omit it so that the first line reads as above.

Transfer the file on a USB key or similar to the desktop of the Asus. Now, back to the terminal:```
cd ~/Desktop
sudo mv brcm*.txt  /lib/firmware/brcm
```Reboot.

---

### Post by abhishekroy49 on 2018-10-14
Thank You

---

