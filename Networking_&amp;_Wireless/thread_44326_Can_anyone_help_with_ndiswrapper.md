---
title: "Can anyone help with ndiswrapper"
date: 2005-06-25
forum: Networking &amp; Wireless
---

### Post by slysy81 on 2005-06-25
Hi all,

Im following the instructions on the wiki to install this. ndiswrapper -l gives the following:

Installed ndis drivers:
aeiwlnic        driver present, hardware present


However I now need to configure the device in networking. But all I get is options for modem connection and ethernet connection. How can I make the wireless card appear also so that I can configure it?

I used these instructions:
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

### Post by az on 2005-06-25
Is the module loaded?

sudo modprobe ndiswrapper

sudo tail -f /var/log/messages will tell you what happens when you load the module- usually you end up with "device mapped to wlan0" or something...

---

### Post by slysy81 on 2005-06-26
Thanks Azz, I will give that a try and let you know what happens, although I already did the modprobe thing. One strange thing I have also noticed that might be causing this is that Ubuntu wont boot up with my wireless usb adapter connected. The screen just goes into low power mode and so I have to connect it after  booting.

Edit: Here is wha I get from that last command:

Jun 26 10:40:44 localhost gconfd (slysy-7656): Resolved address "xml:readwrite:/home/slysy/.gconf" to a writable configuration source at position 1
Jun 26 10:40:44 localhost gconfd (slysy-7656): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 26 10:40:51 localhost gconfd (slysy-7656): Resolved address "xml:readwrite:/home/slysy/.gconf" to a writable configuration source at position 0
Jun 26 10:43:09 localhost kernel: ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
Jun 26 10:43:09 localhost loadndisdriver: loadndisdriver: main(462): version 1.0rc2 started
Jun 26 10:43:10 localhost kernel: ndiswrapper: driver aeiwlnic (Actiontec,09/24/2002, 2.00.09) added
Jun 26 10:43:17 localhost gconfd (root-7899): starting (version 2.10.0), pid 7899 user 'root'
Jun 26 10:43:17 localhost gconfd (root-7899): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 26 10:43:17 localhost gconfd (root-7899): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 26 10:43:17 localhost gconfd (root-7899): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

---

