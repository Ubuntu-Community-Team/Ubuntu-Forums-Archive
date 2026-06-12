---
title: "can't get wireless to work"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by saltoftheearth on 2008-08-30
I have a toshiba l300 and i just got rid of vista and installed ubuntu Hardy Heron. I can't for the life of me get the wireless to work. this is a big problem as now vista won't reinstall either. Hardy heron runs great though except for the wireless. I've tried alot of things the madwifi drivers don't seem to work and neither do the atheros xp drivers through ndiswrapper. I'm not even sure if i should be using atheros drivers or realtek ones here is some terminal:

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)

any help would be much, much appreciated. It's been driving me crazy!

--just checked the toshiba website, it says i should be using the atheros 7.4.2.75 driver, i downloaded it but there is no .inf file to use in ndiswrapper

---

### Post by james_vanb on 2008-08-30
If you can, download the driver file to a windows computer.  Right click the file and click explore. navigate to drivers for XP - Copy entire contents of file - .inf, .sys and .cat if there is one) to a usb jump drive or cd.  Insert in Ubuntu machine and copy same to a file you create in home.  Then try ndiswrapper.

---

### Post by Tom--d on 2008-08-30
Generaly if its a .exe they are just a cover-up for a .zip (sometimes!)

Copy it over to Ubuntu (usb stick maybe?) and unzip it.
```
unzip /home/username/path/to/filefilename.exe
```

---

### Post by saltoftheearth on 2008-08-30
Thanks, I tried both these methods but i still can't find the .inf files. the .exe won't unzip and exploring in windows just shows me the installers. maybe i am doing something wrong. any other help would be much appreciated.

---

### Post by randcoop on 2008-08-30
It may be you should use a different file.  Look here: [http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4902339&postcount=68](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4902339&postcount=68)

---

### Post by saltoftheearth on 2008-08-30
Thanks, I just found those files and tried to us ndiswrapper on them. the drivers install but it says the hardware is not found. Is there anything else i can try?

---

### Post by james_vanb on 2008-08-30
This site is showing a zip file containing .inf file - Maybe this will open for you - Scroll down to find the version you need:

[http://www.atheros.cz/download.php?atheros=AR5007EG&system=2](http://www.atheros.cz/download.php?atheros=AR5007EG&system=2)

---

### Post by saltoftheearth on 2008-08-30
went out and bought a belkin f5d8073 expresscard. works perfectly with ndiswrapper and drivers provided. $50 bucks and probably saved me another day of headaches.

---

