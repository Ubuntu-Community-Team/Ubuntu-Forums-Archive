---
title: "FTDI Driver Install"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by dolphin_smoken on 2009-09-15
I have a device connected on USB that acts as a serial device:
I tried to download the driver from:
[http://www.ftdichip.com/Drivers/VCP.htm](http://www.ftdichip.com/Drivers/VCP.htm)
for Linux.

I have Ubuntu 7.10 and 9.04 (Linux 2.6.28-11-generic). I've tried in both but the driver does not compile. It gives a lot of errors and warnings. Is there anything I am missing before the compilation (I only installed Ubuntu and gcc and g++). Some of the errors are below:

"...
ftdi_sio.c: In function ‘ftdi_chars_in_buffer’:
ftdi_sio.c:1741: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_read_bulk_callback’:
ftdi_sio.c:1751: error: ‘struct urb’ has no member named ‘context’
ftdi_sio.c:1756: error: ‘struct urb’ has no member named ‘status’
ftdi_sio.c:1758: error: ‘struct urb’ has no member named ‘number_of_packets’
ftdi_sio.c:1759: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1761: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1766: error: ‘struct usb_serial_port’ has no member named ‘open_count’
ftdi_sio.c:1769: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1782: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1793: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c: In function ‘ftdi_process_read’:
ftdi_sio.c:1822: error: ‘struct usb_serial_port’ has no member named ‘open_count’
ftdi_sio.c:1825: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1843: error: ‘struct urb’ has no member named ‘transfer_buffer’
ftdi_sio.c:1846: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c:1851: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c:1852: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c:1865: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c:1880: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c:1880: warning: type defaults to ‘int’ in declaration of ‘_min2’
ftdi_sio.c:1880: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c:1882: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1890: error: too many arguments to function ‘tty_buffer_request_room’
ftdi_sio.c:1956: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c:1959: error: ‘struct urb’ has no member named ‘actual_length’
ftdi_sio.c:1973: error: ‘struct usb_serial_port’ has no member named ‘open_count’
ftdi_sio.c:1986: error: ‘struct usb_serial_port’ has no member named ‘open_count’
ftdi_sio.c:1990: error: ‘struct urb’ has no member named ‘transfer_buffer’
ftdi_sio.c:1990: error: ‘struct urb’ has no member named ‘transfer_buffer_length’
ftdi_sio.c:1995: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_break_ctl’:
ftdi_sio.c:2024: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_set_termios’:
ftdi_sio.c:2041: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:2056: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:2093: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:2106: error: expected ‘)’ before ‘KBUILD_MODNAME’
...
"

Thanks in advance!

---

### Post by 3rdalbum on 2009-09-15
It's better to install the "build-essential" package, as it pulls in everything you need to start compiling. You also need the "linux-headers-generic" package in order to build kernel modules.

Also, if I understand the website correctly, the drivers are already present in kernel 2.6.9 and later (Ubuntu 9.04 uses 2.6.28.). What does the Readme file say about it?

---

