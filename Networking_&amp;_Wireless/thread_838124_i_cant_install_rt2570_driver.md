---
title: "i cant install rt2570 driver"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by xpert73 on 2008-06-23
hallo i need help:

i would like to install rt2570-k2wrlz-1.6.1.tar.bz2 driver, but i have this Problem

can somebody help me please???

xpert73@xpert73-laptop:~/Desktop/rt2570-k2wrlz-1.6.1/Module$ make
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/xpert73/Desktop/rt2570-k2wrlz-1.6.1/Module/rtusb_main.o
/home/xpert73/Desktop/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c: In Funktion »usb_rtusb_probe«:
/home/xpert73/Desktop/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:1964: Fehler: Implizite Deklaration der Funktion »SET_MODULE_OWNER«
/home/xpert73/Desktop/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:1984: Fehler: »struct net_device« hat kein Element namens »weight«
/home/xpert73/Desktop/rt2570-k2wrlz-1.6.1/Module/rtusb_main.c:2015: Fehler: Zu wenige Argumente für Funktion »first_net_device«
make[2]: *** [/home/xpert73/Desktop/rt2570-k2wrlz-1.6.1/Module/rtusb_main.o] Fehler 1
make[1]: *** [_module_/home/xpert73/Desktop/rt2570-k2wrlz-1.6.1/Module] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.24-19-generic'
rt2570.ko failed to build!
make: *** [module] Fehler 1
xpert73@xpert73-laptop:~/Desktop/rt2570-k2wrlz-1.6.1/Module$

---

### Post by Pjotr123 on 2008-06-23
Don't use that file, try first the easy way (will probably work):
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

### Post by chili555 on 2008-06-23
I think you will have much better luck with [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)

I just ran 'make' with no errors and no warnings.

---

### Post by acad1 on 2008-06-23
[http://ubuntuforums.org/showthread.php?t=797823&page=4](http://ubuntuforums.org/showthread.php?t=797823&page=4)

Post #34 gives instructions on how to install rt2570 driver.
I have used it several times recently.

---

