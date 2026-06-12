---
title: "how to connect micromax to ubuntu 13.04?"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by nitin_negi on 2013-10-10
as i run install_linux in terminal it shows permission denied...and sometimes also gives a prior message that unable to mount micromax...i had this micromax netsetter successfully installed  in ubuntu 9.10...then whats wrong in 13.04???..please anyone help...im in serious need.

---

### Post by Kevin McCready on 2013-10-10
Have you tried putting
sudo
before your command? I often do that when i get permission denied and it seems to work. After you do sudo, it will ask for your password.

---

### Post by 3rdalbum on 2013-10-10
> **nitin_negi said:**
> as i run install_linux in terminal it shows permission denied...and sometimes also gives a prior message that unable to mount micromax...i had this micromax netsetter successfully installed  in ubuntu 9.10...then whats wrong in 13.04???..please anyone help...im in serious need.

A couple of things:

1. Usually you don't need to install a driver to use a 3G modem. Have you just tried going to the Network Manager icon on the top panel, going to Edit Connections and then adding a new Mobile Broadband connection? You probably already have the right driver.

2. If that doesn't work, then make sure the "install_linux" file has execute permission, and you will definitely need to run it with sudo:

```
sudo chmod a+x <drag file to the terminal and hit Enter>
sudo <drag file to the terminal and hit Enter>
```

---

### Post by mörgæs on 2013-10-10
I have to ask you to stop multiposting.

This is your 4. thread on the same topic. Your other threads have been jailed.

---

### Post by fantab on 2013-10-10
> **nitin_negi said:**
> as i run install_linux in terminal it shows permission denied...and sometimes also gives a prior message that unable to mount micromax...i had this micromax netsetter successfully installed  in ubuntu 9.10...then whats wrong in 13.04???..please anyone help...im in serious need.
Post the output of:

```
lsusb
```

We have to make sure if your modem is being detected as modem or a storage device. 
There seems to be a bug in either NetworkManager or 'usb-modeswitch' which is preventing the switch for certain USB modems. I have a ZTE modem that has a mind of its own when used in Linux. It works well in Windows though.

---

