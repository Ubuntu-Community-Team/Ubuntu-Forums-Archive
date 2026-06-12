---
title: "&quot;wifi conections&quot; pops up on the networks thing on the system tray but wont show wifi"
date: 2014-03-01
forum: Networking &amp; Wireless
---

### Post by katja2 on 2014-03-01
hello. the network tab on the system tray says "wifi connections" when i plug in my wifi chip (i don't know what chipset it is) but no BSSIDs show up. i can'T connect to anything. i'm on a Dell Latitude D620 and the native wifi chip doesn'T work either. do es anyone have any advice? i'm running xubuntu and it says the broadcom driver was installed.. but the next time i checked the additional drivers, nothing was there.

---

### Post by varunendra on 2014-03-03
Welcome to the forums katja2!

While your USB adapter is plugged in, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It should give us all the info required to troubleshoot one or both of the wifi cards.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by katja2 on 2014-03-03
here you go. thanks for replying

---

### Post by varunendra on 2014-03-04
Both your internal and USB adapters can be made to work. Let's try the internal one first (remove the USB adapter and keep it removed while trying the internal one).

With a wired connection, please run the following commands in a terminal -
```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo apt-get install linux-firmware-nonfree
```
One or both of the second and third commands may return error (like "no such file.." etc.), just ignore if they do, and proceed with the next ones.

Reboot and see if you can scan and connect to the wireless networks now. If you can, let me know if you need to troubleshoot the USB one also.

---

### Post by katja2 on 2014-03-05
thanks so much!!! i couldn'T get the internal wifichip to work but the external one magically works :3 thanks a bunch!

---

### Post by varunendra on 2014-03-05
Umm.. that's indeed magic, because what I suggested was supposed to help the internal card, not the USB one.

If the problem reoccurs, please post back with a fresh wireless_script report. It should tell us the logic behind the 'magic'. :)

---

