---
title: "Linksys Compact Wireless G WUSB54GSC"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Troll_1988 on 2009-07-06
Hi I just switched from Vista to Ubuntu yesterday and ive been trying all night to get my Linksys Compact Wireless G USB network adapter to work for Ubuntu. But its not working I installed Ndiswrapper and got the driver from the install CD the usb network adpater came with and it still aint working it keeps saying invalid driver and its very frustrating so any help will be greatly appreciated

---

### Post by kerry_s on 2009-07-06
are you sure you installed ndiswrapper right?
are you pointing it to the right *.inf file?

you can try grabbing the gui for ndiswrapper, it's called "ndisgtk" it's in the repo to.

can you run-> **lsusb** <-with it plugged in, put the output here so we can see what kind of driver it needs.

on my linksys card all i had to do was install b43-fwcutter & reboot, it **might** be that simple for you. ;)

---

### Post by Troll_1988 on 2009-07-06
when i typed lsusb it said
 
 
Bus 001 Device 005: ID 13b1:0026 Linksys
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 046d:c227 Logitech, Inc.
Bus 002 Device 004: ID 046d:c226 Logitech, Inc.
Bus 002 Device 003: ID 046d: c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 002 Device 002: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
Thanks in advance

---

### Post by Troll_1988 on 2009-07-06
Bump and if it would be easier maybe some one can just contact me thru aim. Im on there now my S/N is kript1988 thanks agian

---

### Post by kerry_s on 2009-07-06
man that only tells me it's linksys. try posting your /var/log/dmesg

---

