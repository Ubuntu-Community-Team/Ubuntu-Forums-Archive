---
title: "Broadcom BCM4352 802.11ac Wireless Adapter not working"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by M._Shearer on 2014-12-31
I'm not new to Linux (Fedora) but I am new to Ubuntu. For Christmas, my wife got me a new laptop. 8-) It's a Lenovo Yoga 3Pro and very nice but no computer is worth anything until it runs Linux. I did a dual boot Win8.1 and Ubuntu 14.04 using [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) as a guide. The install went fine (without internet connection) and the wireless worked on the reboot. I then did updates and after that reboot I didn't have wireless.

Not sure where to go now but I saw your forum and thought you could help. i followed your instructions and re-did the updates and then ran your script. I have attached the output from the script. Help would be greatly appreciated.

---

### Post by jeremy31 on 2014-12-31
Since ```
rfkill list
``` shows a hard block on wifi, try this ```
sudo modprobe -r ideapad_laptop
``````
sudo rfkill unblock all
``` and see what ```
rfkill list
``` shows

---

### Post by M._Shearer on 2014-12-31
I ran the above commands and then iwlist scam...
*********
wlan0     Scan completed :
          Cell 01 - Address: 9E:C6:5D:04:F9:0C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:off
                    ESSID:"LinuxDude"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 527476ms ago
                    IE: Unknown: 00094C696E757844756465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A2D1817FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD09001018020000100000
                    IE: Unknown: DD070050F202000100
*********

My router uses channel 11 but wlan0 is set to 1. How do I change the channel? Will these changes persist for my next reboot?

---

### Post by M._Shearer on 2014-12-31
OK, I did a iwlist wlan0 scan and now I can ping Woohoo!!! Should I try a reboot?

---

### Post by jeremy31 on 2014-12-31
> **M._Shearer said:**
> OK, I did a iwlist wlan0 scan and now I can ping Woohoo!!! Should I try a reboot?

Do this before rebooting ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad_laptop.conf
```

And a side note: are you dual booting with windows?  I would like to know what hex file is needed for bluetooth to work on that

---

### Post by M._Shearer on 2014-12-31
I thought I would have to blackllist it. I found a link that talked about the ideapad_laptop and making some changes. Currently it make the computer think it's in airplane mode. I'll have to see what fixes are required. Yes, I'm dual booting with Win8.1. Let me know what file you would like.
Thanks for your help

---

### Post by jeremy31 on 2014-12-31
See if a file named bcbtums-win8x64-brcm.inf exists on your 8.1 install and see if you can find "e07a" in it as it is the key to get bluetooth working correctly in Ubuntu

---

### Post by M._Shearer on 2014-12-31
Yup, it's there...

%BRCM20702Bt.DeviceDesc%=BlueRAMUSBE07A,        USB\VID_0489&PID_E07A       ; Lenovo China 4352+20702 NGFF

%BRCM20702Bt.DeviceDesc%=RAMUSBE07A,        USB\VID_0489&PID_E07A       ; Lenovo China 4352+20702 NGFF

[RAMUSBE07A.CopyList]
bcbtums.sys
btwampfl.sys
BCM20702A1_001.002.014.1443.1496.hex

---

### Post by jeremy31 on 2015-01-01
> **M._Shearer said:**
> Yup, it's there...

%BRCM20702Bt.DeviceDesc%=BlueRAMUSBE07A,        USB\VID_0489&PID_E07A       ; Lenovo China 4352+20702 NGFF

%BRCM20702Bt.DeviceDesc%=RAMUSBE07A,        USB\VID_0489&PID_E07A       ; Lenovo China 4352+20702 NGFF

[RAMUSBE07A.CopyList]
bcbtums.sys
btwampfl.sys
BCM20702A1_001.002.014.1443.1496.hex

If you want to try to get bluetooth going, try this
```
git clone git://github.com/jessesung/hex2hcd.git
```
```
cd hex2hcd
```
Copy the BCM20702A1_001.002.014.1443.1496.hex into the hex2hcd folder, probably easiest to search for it in Win8 and copy it to a USB drive and then boot into Ubuntu
```
make
```
```
./hex2hcd BCM20702A1_001.002.014.1443.1496.hex fw-0489_e07a.hcd
```
```
sudo cp fw-0489_e07a.hcd /lib/firmware/
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```
If no signs of bluetooth after that ```
dmesg | grep firmware
```

---

### Post by M._Shearer on 2015-01-01
Thanks for the help. I think we can say my problem is SOLVED. 8-)

---

