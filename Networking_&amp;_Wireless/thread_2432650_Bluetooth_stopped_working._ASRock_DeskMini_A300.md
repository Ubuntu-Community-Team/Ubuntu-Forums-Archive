---
title: "Bluetooth stopped working. ASRock DeskMini A300"
date: 2019-12-05
forum: Networking &amp; Wireless
---

### Post by grahaml2 on 2019-12-05
Ubuntu 19.10
ASRock DeskMini A300
 
 
 Bluetooth was working but after a app crash (0 A.D.) Bluetooth stopped working (both mouse and keyboard).
 I’ve only recently started using Ubuntu (was previously a W10 user) and am more than a bit lost with using the terminal and command line, however after a bit googling I do know the below.

 
 
 graham@graham-desktop:~/Desktop$ bluetoothctl --version
 bluetoothctl: 5.50
 graham@graham-desktop:~/Desktop$ sudo rfkill list
 [sudo] password for graham:  
 0: phy0: Wireless LAN
     Soft blocked: yes
     Hard blocked: no
 283: hci0: Bluetooth
     Soft blocked: no
     Hard blocked: no
 
 
 Settings>Bluetooth informs me that NO Bluetooth dongle is found and that Bluetooth is turned off, even though a Bluetooth dongle is connected, trying to turn on Bluetooth fails.

 The googling results gave me various command line things to try, non of them fixed the problem though strangely the mouse started to work, even though Settings>Bluetooth still says no dongle found and Bluetooth is switched off. If I remove the dongle the mouse stops working, replacing it the mouse works again.
 
 
 Bluetooth Manager ‘Adapter’ and ‘Device’ are greyed out.
 
 
 Looking at a few other posts in the networking forum I see that I’ll probably be asked to run   wildmanne39’s script, that I have done

 the pastebin url
 [https://pastebin.com/Rtmg69u1](https://pastebin.com/Rtmg69u1)
 
 
 If anyone can help it will be appreciated
 
 
 Graham

---

### Post by grahaml2 on 2019-12-06
An update. this morning (after being switched off all night) an improvement, now in settings>Bluetooth Bluetooth is switched on and 'Bluetooth Keyboard' is shown as disconnected, Blueman after going through the connect routine shows the keyboard as 'device added successfully, but failed to connect'.
The mouse is not shown in settings>Bluetooth or Blueman, it just works regardless. 

So an improvement but not a complete fix

---

### Post by grahaml2 on 2019-12-06
another and last update.
Both the keyboard and mouse are now working, every time i rebooted something would start working, first the keyboard and then the mouse. Strangely the keyboard works with one dongle and the mouse with another, they wont both work with the same dongle.

---

