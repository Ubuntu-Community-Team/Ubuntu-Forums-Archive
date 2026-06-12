---
title: "bluetooth gone awol Ubu 16.05"
date: 2018-08-14
forum: Networking &amp; Wireless
---

### Post by pedro_rodriguez2 on 2018-08-14
A sad story: home from holiday in Spain, I want to send some photos from my mobile to this laptop. Worked before the holiday. Bluetooth won't switch on on the laptop. 

I followed these instructions, which worked for me previously:

> **1. Start the bluetooth daemon**

 Go to your terminal and type :
 sudo /etc/init.d/bluetooth start **2. Reinstall packages**
 If this doesn't work, go to your terminal and type :
 sudo apt-get purge blueman bluez-utils bluez bluetooth
sudo apt-get install blueman bluez-utils bluez bluetooth Then run :
 sudo /etc/init.d/bluetooth start

Purging bluetooth had a strange effect: System Settings was lost! The Ubu 16.05 install was broken, though still running

I decided to upgrade to 18.04 from the software manager. Took a while, but it got there.

Seems now, the reason bluetooth will not start is because there is no bluetooth adaptor (see screenshot). Maybe it broke while I was on holiday, but the the laptop was unplugged and off.

Is there any way to get the bluetooth adaptor going again?

---

