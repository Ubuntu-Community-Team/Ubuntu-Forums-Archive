---
title: "Wireless on Sony Vaio (very old model)"
date: 2017-02-02
forum: Networking &amp; Wireless
---

### Post by 4l3x2 on 2017-02-02
Good morning.

This time I installed XUbuntu 16.04 on the laptop of a colleague of mine, dual boot with Windows Vista ....

The laptop is an old Sony Vaio, here are the specs:
Intel Core Duo T5500
2Gb Ram DDR2
HD 120Gb
Intel 9345ABG wlan (disabled)
VE Intel eth0
Nvidia GeForce Go 7400

The first thing I noticed was the wireless disabled, but since my colleague didn't know that his laptop has a wireless card and bought a Usb dongle, I decided to install the latter.

If I type
tail -f /var/log/kern.log

and plug the dongle in, the system recognizes a Realtek wireless usb device and doesn't install the correct module.
At this time i tried:
rmmod iwl3945
rmmod iwlegacy
downloaded dkms[etc...].deb and rtl8192cu-dkms.deb and installed them with dpkg -i [both .deb]
finally I wrote
modprobe rtl8192cu

but the wlan still doesn't work...
I also tried to reset the network hardware with
service network restart (or something similar, I found the correct line online)

Now, I'd like to enable both the built-in card and the usb dongle, how can I do?

Thanks in advance for your help, of course.
Alex

---

### Post by slickymaster on 2017-02-02
Moved to the **Networking & Wireless** sub-forum

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.

---

### Post by 4l3x2 on 2017-02-03
Here it is
The Usb Wi-Fi dongle was plugged in

---

### Post by praseodym on 2017-02-04
The card is turned off, see "rfkill list".

Please show

```
lsmod
```

completely. Any button/switch key or key combo?

---

### Post by 4l3x2 on 2017-02-06
Ok, I found the wireless hardware switch and put it on, but still rfkill says it is off.
The bios doesn't contain any option about wireless and the system starts with WiFi Enable disabled, I had to set it manually on.
Please find attached the output of the commands.

---

### Post by praseodym on 2017-02-06
Try resetting the BIOS to default settings

---

### Post by 4l3x2 on 2017-02-06
Tomorrow morning I'll try :-)

---

### Post by 4l3x2 on 2017-02-07
No results... :-(

---

### Post by praseodym on 2017-02-07
If there is a button or switch then reboot and press it permanently or repeatedly

---

### Post by Hadaka on 2017-02-07
Hi, please post the output of..
```
sudo dmidecode -s bios-release-date
sudo dmidecode -s system-product-name
```
This will give us needed information on your Sony Vaio

*In the event you are curious about additional system information..
```
sudo dmidecode -s <valid string keyword>
```

Valid string keywords are:
  bios-vendor
  bios-version
  bios-release-date
  system-manufacturer
  system-product-name
  system-version
  system-serial-number
  system-uuid
  baseboard-manufacturer
  baseboard-product-name
  baseboard-version
  baseboard-serial-number
  baseboard-asset-tag
  chassis-manufacturer
  chassis-type
  chassis-version
  chassis-serial-number
  chassis-asset-tag
  processor-family
  processor-manufacturer
  processor-version
  processor-frequency

---

### Post by 4l3x2 on 2017-02-09
Here they are, thank you :KS

---

### Post by Hadaka on 2017-02-09
Thanks, from the data you provided it appears you have...
A 2007 Sony Vaio VGN-AR31E . This link to the user manual shows..
[https://www.manualslib.com/manual/248715/Sony-Vgn-Ar31e.html?page=16](https://www.manualslib.com/manual/248715/Sony-Vgn-Ar31e.html?page=16)
Wireless physical switch #15 marked "O" in the user manual page 16.
You may possibly have a keyboard wifi on/off key combination. look for ..
"FN" key..usually lower left..and a "Wifi Signal" key usually an "Fnumber" key
top row..check F1 thru F12 for a key that has a symbol that looks like this (((A)))
Press the FN key and the F?((A)) key to turn on/of wireless. Press one time and then do..
```
rfkill list all
```
 To see if the hard block clears.Until that block is cleared there is nothing we can do to get
your wireless functioning.
Thanks.

---

### Post by 4l3x2 on 2017-02-10
Thank you, I found the problem:
the phisical switch....

There is no Fn+<key>, only the phisical switch and it's working bad, I have to open the pc and fix it.

---

### Post by Hadaka on 2017-02-10
Hi, Glad you found the problem. Since that computer is older 2007
you may find 16.10 a bit much for it,and the life of 16.10 is rather
short. 14.04 LTS or 16.04 LTS would probably be a better choice and perhaps
Lubuntu instead of Ubuntu. Just a suggestion. Good luck with your repair.
Thanks for marking your post solved.

---

