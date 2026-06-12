---
title: "Need help with 802.11ac drivers"
date: 2018-06-30
forum: Networking &amp; Wireless
---

### Post by pootaholic on 2018-06-30
I am running Ubuntu 12.04 and need help with installing USB Network Adapter. Seems everywhere I have turned I've run into problems, mostly that the drivers are either not available or are for a more updated version of Ubuntu.

Although I am new to Linux, I am reasonably comfortable using the system and the terminal app. ATM I have nothing recognised by the system although I have run dmesg, lsusb and iwconfig and attached the results.

TIA ... Dave

---

### Post by praseodym on 2018-06-30
Hi,

12.04 is outdated! Please install 16.04 LTS or 18.04 LTS. Even upgrading to 14.04 makes no sense with this new device. Driver is rtl8812AU

---

### Post by pootaholic on 2018-06-30
Yes, I'm aware of more up-to-date releases, but I am using this version as it supports Linuxcnc, some of the other releases do not support this application.

---

### Post by praseodym on 2018-06-30
[http://linuxcnc.org/](http://linuxcnc.org/) New version of linuxcnc is out.

---

### Post by pootaholic on 2018-06-30
Yes, I am running Linuxcnc Ver. 2.7.14

---

### Post by praseodym on 2018-07-01
Why not installing 18.04 parallel to 12.04 to test linuxcnc with that? If it works...

---

### Post by pootaholic on 2018-07-01
Linuxcnc has not been tested with that version and therefore is not recommended.

---

### Post by praseodym on 2018-07-02
Why not testing it or contacting the developers? Maybe they can help with virtual machines?!

---

