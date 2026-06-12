---
title: "Bluetooth recognises cell phn but will not connect"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by jbb on 2008-02-28
both my cell phone and my laptop using bluetooth dongle can see each other (screen show device name)  can pair to laptop and xfer password.  Get "obex://[00:0e:6d:68:c5:ac]" is not valid location  error when I try to connect from laptop and cellphone also gives "fail to connect" error.
Saw a similar question on this forum.  Has anybody got any ideas or suggestions?
I connect to internet via a Huawei 220 modem and I use Gutsy.

Thanks John

---

### Post by jvanoort05 on 2008-02-29
what type of bluetooth device are you useing in your computer? is it a usb device or is it a built-in bluetooth?

---

### Post by Cresho on 2008-02-29
[http://ubuntuforums.org/showthread.php?t=94713&highlight=Bluetooth+obex](http://ubuntuforums.org/showthread.php?t=94713&highlight=Bluetooth+obex)

you also need to find out if your unit is obex compatible.  There are tons of tutorials out there and I can use konqueror to view my cellphone like a hardisk and transfer files like nothing.  Learning curve is steep for newbies if your not familiar with regular windows...etc.

---

### Post by ankscorek on 2008-02-29
remember to use the file sharing module along with obex push and receive

---

### Post by jbb on 2008-02-29
> **Cresho said:**
> [http://ubuntuforums.org/showthread.php?t=94713&highlight=Bluetooth+obex](http://ubuntuforums.org/showthread.php?t=94713&highlight=Bluetooth+obex)

you also need to find out if your unit is obex compatible.  There are tons of tutorials out there and I can use konqueror to view my cellphone like a hardisk and transfer files like nothing.  Learning curve is steep for newbies if your not familiar with regular windows...etc.

Thanks for info     very usefull    downloaded a few extra files   Now it works
even better then on windows   
Found that I need to pair phn to pc then I can connect and transfer data

1x again many thanks
John Britz

---

### Post by Cresho on 2008-03-01
yeah, when you tell the phone to pair with the operating system, a pop up appears and it allowes you to pair.  I noticed my bluetooth icon in my bar has a few new options.  I have not tried updating my instructions but ill post here.  Its just a little something I have gathered.
[HTML]********************************************************************************
********************************************************************************
********************************************************************************
bluetooth***********************************************************************
********************************************************************************
bluetooth analyzer
kbtobexclient
bluetooth obex server
kbluetooth
kbluemon
sudo aptitude install bluez-passkey-gnome



more bluetooth



I just dont know where to post it, so please feel free to move it. Comments appreaciated


Mission: Use Bluetooth to access the Files on my Mobile Phone, and to use my Bluetooth Headset with Skype - in 3 Chapters


PART 1: Copy Files from and to Mobile Phone (K700i) - simple

1. Install bluez-utils
2. Install kdebluetooth (gnome bluetooth is not as far developed as kde I think), libopenobex, qobex
3. Install konqueror
4. Check /etc/bluetooth/hcid.conf:
security should be user
pairing should be multi
pin_helper should be /usr/bluez-pin
5. restart bluez-utils /etc/init.d/bluez-utils restart
6. start kbluetoothd (it sometimes needs to be startet twice on my machine until the icon shows up in the System Notifications Tray)
7. Enable Bluetooth on your Device (Mobile Phone etc.)
8. If you click on the kbluetoothd Icon, konqueror will show up with "bluetooth:/" location, listing all BT Devices found
9. Click on your Device (sometimes only the MAC-Adress shows up), konqui will list all supported Services, and start using the Service (for my Mobile, K700i its obex File Transfer, then I can browse my Mobile like a Disk Drive, copying what I want). Previous to that, my phone wants to pair with my PC, aksing for a PIN. Just guess one (1234), after that a popup on the PC should occour, asking for the same PIN.
10. You could also send Files from the Phone to your PC, then a popup will show up, asking you, if you wish to receive the file.[/HTML]

---

