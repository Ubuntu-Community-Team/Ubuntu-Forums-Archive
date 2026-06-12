---
title: "gtkterm does not respond for serial connection"
date: 2020-01-11
forum: Networking &amp; Wireless
---

### Post by jaraqui2 on 2020-01-11
I have a Xubuntu guest on a Windows 10 host and I need to establish a serial communication between my notebook and the external system via serial connection. 
Notebook side is an USB port and the system side is a true serial DB-9 connector.
I already tried picocom and gtkterm. Both of them do not show any result on their console screens (picocom and gtkterm screeens).
The serial connection is recognized by the Xubuntu because it appears the /dev/ttyUSB0 file.
When I instruct gtkterm to echo the results on a file, it only shows me a ^@ character inside the file each time the system is executed.

The communication works on another notebook which is Windows 7 (without virtualbox). At this arrangement I use the old Windows hyperterminal and the messages appear on the screen of this software.

Any help will be appreciated.

---

### Post by jaraqui2 on 2020-01-14
Just an update: 

1) I changed the visualization from ascii to hexadecimal and gtkterm shows me a zero byte, #00 each time I run the application.

2) I tried also with minicom and putty. All of them behave the same way, i.e., nothing is showed on the screen.

---

