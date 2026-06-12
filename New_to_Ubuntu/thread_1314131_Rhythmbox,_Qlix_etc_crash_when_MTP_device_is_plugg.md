---
title: "Rhythmbox, Qlix etc crash when MTP device is plugged in"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by uvoli on 2009-11-04
I'm using Ubuntu 9.04, and have after several attempts managed to get it to recognise my Samsung YP-S3 mp3 player, which is an MTP device. I've added the latest mtplib packages etc, and added rules relating to this particular player. I can connect to the device through the terminal, read the contents, and add files one at a time using mtp-sendfile command. However, as soon as I try to open Qlix or Rhythmbox to add music to the device, the applications crash. These applications run fine when the device isn't attached. I don't know if the log readout will be any help:

rhythmbox[20670]: segfault at 800909b5 ip b6ec590e sp bfbabd70 error 6 in libglib-2.0.so.0.2000.1[b6e8e000+b6000]

graham-laptop kernel: [ 4033.924128] usb 1-5: reset high speed USB device using ehci_hcd and address 5
Nov  4 14:19:25 graham-laptop kernel: [ 4034.056895] qlix[25620]: segfault at 1 ip 08065701 sp b55e01bc error 4 in qlix[8048000+a5000]


If anyone has any ideas, I'd be very grateful - it's frustrating that I've managed to get it to connect, & that I can even add & remove files using the terminal, but can't get it to open with Rhythmbox etc. It's a slow process adding songs one at a time...

---

### Post by caffein on 2009-12-25
Hi, I am the developer for Qlix. Could you please run qlix from the command line and copy/paste the command line output for the program? Alternatively, you can email it to me as well.
Thanks!
Ali

---

