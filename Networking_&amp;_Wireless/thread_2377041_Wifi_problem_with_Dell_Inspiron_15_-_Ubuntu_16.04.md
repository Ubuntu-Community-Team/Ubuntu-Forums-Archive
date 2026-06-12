---
title: "Wifi problem with Dell Inspiron 15 - Ubuntu 16.04"
date: 2017-11-08
forum: Networking &amp; Wireless
---

### Post by manover2 on 2017-11-08
Hello there.
I've just bought a Dell Inspiron 15 with Ubuntu 16.04 already installed but I cannot connect to my WiFi.
I can see the network but once I try to connect there's no way. ](*,)
I've got this Network controller:

> 
01:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)


I've launched the wireless-info script and here's the result: 

[https://paste.ubuntu.com/25919145/](https://paste.ubuntu.com/25919145/)

It seems there is an issue with ath10k firmware so I've read on the forum for similar issues: I did what suggested in "*[SOLVED] 16.04 wireless not working"* but without success.

Can anyone help me?
cheers,

---

### Post by praseodym on 2017-11-08
Firmware update via cable:

```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

### Post by manover2 on 2017-11-10
Hello praseodym, 
thanks for your answer!
I've already did the firmware upgrade via cable, as you suggested. 
The wireless-info file I attached has been generated after that operation.
Unfortunatelly the wifi is still not working.

Any idea?
cheers,

---

### Post by praseodym on 2017-11-10
Forgot the file?

---

### Post by manover2 on 2017-11-11
Hello,
I've put it here:

[https://paste.ubuntu.com/25919145/](https://paste.ubuntu.com/25919145/)

---

### Post by praseodym on 2017-11-11
Firmwareupdate:

```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot. Change the channel in your router to "6"

---

### Post by manover2 on 2017-11-12
Thanks. Unfortunately still nothing. WiFi still not working. I see the network but it refuses to connect to it.
](*,)

---

