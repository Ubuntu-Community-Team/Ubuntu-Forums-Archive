---
title: "Basic bluetooth help"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2007-05-22
I have a Toshiba Libretto U100 with bluetooth. I have never really used bluetooth, so please start from zero. I am trying to use bluetooth headphones right now, but I would like to understand how bluetooth works so I know have to use all the features. I have looked for howtos but didn't find much that helped. I ran kbluetoothd from the command line and since then I have the bluetooth icon in my system tray. When I click on it it says no adapters found. If I try and change any settings via that app or the system settings app, I get an error about no dcop services. Any assistance is appreciated.

---

### Post by spd106 on 2007-05-24
Sorry I don't have bluetooth myself, all I can do is point you towards the documentation wiki. [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by lingenfr on 2007-05-24
Thanks. I started with that. My adapter is not detected. The output from lsusb is:

Bus 004 Device 004: ID 0930:1200 Toshiba Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0766:5401 Jess-Link Products Co., Ltd
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 08ff:2580 AuthenTec, Inc.
Bus 001 Device 003: ID 15ca:00c3
Bus 001 Device 001: ID 0000:0000

I believe the Jess-Link device is my bluetooth adapter. I found one web posting that indicated that the kernel had to be patched to make this work, but the patches were for an older kernel version, so I didn't try it. When I try hcitool dev, I get nothing. I am wondering why I can't build the appropriate module for this and load it rather than patching the kernel.

---

### Post by spd106 on 2007-05-25
All I can find is this website about toshset [http://www.schwieters.org/toshset/](http://www.schwieters.org/toshset/)

As far as I can tell the toshiba_acpi module is included in Ubuntu, so it should already have been loaded.

---

### Post by lingenfr on 2007-05-25
You da man. Toshset worked like a champ. I ran:

sudo ./toshset -bluetooth on

and the tray popup said the adapter was found. Toshset looks like a pretty useful tool. I fired up my bluetooth headphones, but they would not pair with the U100. I will continue looking. Looks like maybe I need to find or create a profile. I tried the headset profile, but no joy. Thanks a lot for getting me this far.

---

### Post by spd106 on 2007-05-26
I should mention that I found the link through the Laptop Testing Team in the Ubuntu wiki. There are some similar Toshibas listed though none of them appear to be from the Libretto line.
[https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba](https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba)

If you can spare some time it would be nice if you could contribute an entry for your model. It doesn't have to be particularly detailed, just mention the main sticking points and possible solutions. There is a guide to creating new pages here [https://wiki.ubuntu.com/LaptopTesting](https://wiki.ubuntu.com/LaptopTesting)

Good luck on your investigations

---

### Post by lingenfr on 2007-05-26
Started:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaLibrettoU100](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaLibrettoU100)

---

