---
title: "Cannot read from serial port, usb to serial"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by willydlw on 2009-04-07
Have kubuntu 8.10 installed on an HP dv6000 series laptop. Have some c++ code where I need to read and write to a serial port connection. The code runs perfectly on a friend's gentoo machine. When we run it on my machine, open works for our serial port class, but it fails on read every time. read returns a -1 and error is temporarily unavailable.

Am using a Prolific usb to serial adapter cable on my machine. Adapter and serial cables both work fine on friend's machine. Also, cannot connect with minicom.

I am a member of groups tty and dialout, I have rw permission and we have tried running the code as root to no avail. How can I get usb to serial connectivity?

Here's my groups:

diane@diane-laptop:~$ groups
diane root bin sys adm tty proxy dialout fax cdrom floppy sudo audio dip backup src video plugdev games users scannerfuse ssh lpadmin netdev admin sambashare

When I plug in the usb to serial, here's dmesg:

diane@diane-laptop:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[ 1061.580603] usb 4-1: pl2303 converter now attached to ttyUSB0

Here's /dev/ttyUSB0 

diane@diane-laptop:/dev$ ls -al ttyU*
crw-rw---- 1 root dialout 188, 0 2009-04-07 16:01 ttyUSB0

Then I have tried chmod 

diane@diane-laptop:/dev$ sudo chmod a+rw /dev/ttyUSB0
[sudo] password for diane:
diane@diane-laptop:/dev$ ls -al ttyU*
crw-rw-rw- 1 root dialout 188, 0 2009-04-07 16:01 ttyUSB0

Still not able to connect serial port. What else do I need to enable so that I can have usb to serial connectivity?

Thanks for your help and advice.

Willy

---

### Post by cmnorton on 2009-04-11
It's been years since I did anything with com ports, and even then it was on Windows not Unix/Linux. Do you or your application (setuid) have to be root to access the port? I don't know off hand. To mount a volume, you have to be root, unless fstab is configured otherwise. I'd search for COM (serial) port permissions and see what comes up.

---

