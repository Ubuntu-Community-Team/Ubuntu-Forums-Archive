---
title: "acer e1 510 wifi button not working"
date: 2014-07-23
forum: Networking &amp; Wireless
---

### Post by radu7 on 2014-07-23
Hello. I have recently bought an acer e1 and tried to install different versions of ubuntu on it, in order to make that button work, because it didnt even see a wifi interface. I tried lubuntu 12.04, ubuntu 12.04, linux mint 9 and neither of them worked. I tried ifconfig on terminal and wlan0 didnt show up, as it should.
I entered the bios and tried both options of fn keys, whic are " special keys" and " function keys" but wifi button not worked, even though some special fn keys such as volume up and down, monitor turn off,brightness,etc.. worked fine when i presed fn.
And if i cannot make that button work i wolud like to know if there is another way to make the computer "see" the fact that i have a wireless card and use it properly.
Can anyone help me?

---

### Post by westie457 on 2014-07-23
Hello radu7 and welcome to the Forum.

Could you open a terminal (Ctrl+Alt+T is the quick way) and run these two commands. ```
lspci -nnk | grep net

rfkill list all
```
Post the output back here so we know what we are dealing with.

Thank you.

---

### Post by radu7 on 2014-07-23
[ATTACH=CONFIG]254944[/ATTACH]

---

### Post by praseodym on 2014-07-23
Hi,

"lspci" only shows the LAN device. Lets check:
```

lsusb >> wlan.txt
pccardctl info >> wlan.txt
lsmod >> wlan.txt
ifconfig -a >> wlan.txt
iwconfig >> wlan.txt
cat /etc/resolv.conf >> wlan.txt
```
Upload the file "wlan.txt" from your /home directory here

---

### Post by radu7 on 2014-07-23
ok, here is the file wlan.txt and also had an idea that wifi card might not be there and installed sysinfo, and took a picture of network thta you might want to see because there is no wirelesss card info listed.
ON my other laptop, i also installed sysinfo and it shows the info such as "wireless card intel..etc", so this might mean that the new laptop may not have wireless?[ATTACH]254945[/ATTACH][ATTACH=CONFIG]254946[/ATTACH]

---

### Post by praseodym on 2014-07-23
Ok, the WLAN driver is not loaded and there a re no nameservers listed. Lets check:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
sudo modprobe -v ath9k nohwcrypt=1
```
Try to connect and check the buttons. If the buttons do not work, try:
```

sudo modprobe -v acer_wmi wireless=1
```
Check afterwards the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
dmesg | grep ath9k
```
Check also the BIOS settings if wireless can be activated there, and if the network can be booted before the OS

---

### Post by radu7 on 2014-07-23
Finaly i solved it.
I just tried another linux distribution, zorin os7 and worked perfectly, including wifi.
So i guess the other ones didnt have the driver required to use the wifi card.
Anyway thank you for the support and quick answer.

---

