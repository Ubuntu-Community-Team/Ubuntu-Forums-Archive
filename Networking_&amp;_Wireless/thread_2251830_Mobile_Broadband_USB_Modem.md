---
title: "Mobile Broadband USB Modem"
date: 2014-11-06
forum: Networking &amp; Wireless
---

### Post by lce67 on 2014-11-06
This is my first post... hope it will help....

In 12.04 usb modem worked out of the box... Not so when i replaced 12.04LTS with 14.04LTS...It was reconized as modem but would not connect or show when setting up broadband connt in manager...i read and read and read........and after a week of trying suggestions and many reinstalls today success Wahoo!!

if you have changed any of the usb_modemswitch files or networkmanager files
you will need to reinstall..... fresh

then just remove modemmanager that came with 14.04LTS and install modemmanager_0.5.2.0 from 12.0.4.5LTS

first download modemmanager from ubuntu packages site be sure to get the one from 12.0.4.5LTS 
copy it from downloads to home 

open term and uninstall modemmanager with this command

sudo apt-get purge modemmanager

still in term type 

ls

make sure the modemmanager pkg you downloaded is listed it
should be modemmanager_0.5.2.0-0ubuntu2_amd64.deb for 64bit installs
i386 for 32bit installs

then type

sudo dpkg -i (name of pkg you downloaded)

connect your usb modem and set up connection

Yaaaa connected!!!

---

