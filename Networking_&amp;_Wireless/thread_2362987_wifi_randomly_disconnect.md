---
title: "wifi randomly disconnect"
date: 2017-06-04
forum: Networking &amp; Wireless
---

### Post by migoo2 on 2017-06-04
[COLOR=#000000][I]please guys i have a problem  my wifi disconnects frequently and i need to desactivate and activate network to reconnect  this is very frustring can you help me plz ?
[/I][/COLOR]
```
output iwconfig

lo        no wireless extensions.



wlp3s0f0  IEEE 802.11bgn  ESSID:"Migo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 9C:B2:B2:E2:E2:6C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:3   Missed beacon:0
```

---

### Post by wildmanne39 on 2017-06-04
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by wildmanne39 on 2017-06-04
*Thread moved to **Networking & Wireless**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by migoo2 on 2017-06-04
ok bro i did it [https://pastebin.com/V0RQj04q](https://pastebin.com/V0RQj04q)

---

### Post by wildmanne39 on 2017-06-04
Please do by copying and pasting the code one line at a time and hitting enter after each line :
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Set your network settings in network manager to match the screenshots.

Go into your router and change the encryption to just WPA2 if you have that option.
Reboot computer.

---

### Post by migoo2 on 2017-06-04
i did it , i will test and say you thank you bro

---

### Post by wildmanne39 on 2017-06-04
If it still disconnects run the wireless script again and let us see the new file created.

---

### Post by migoo2 on 2017-06-05
yes :( it still disconnects [https://pastebin.com/mnuS3hCd](https://pastebin.com/mnuS3hCd)

---

### Post by wildmanne39 on 2017-06-05
Will your power management was off in the first report, so I did not recommend turning it off, but now it is on so we will turn it off.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Did it disconnect with you setting in the same place with your computer or did you get further away from the router?
Reboot

---

### Post by migoo2 on 2017-06-05
i did it , and yes bro it's in the same place , i will test and see now ty

---

