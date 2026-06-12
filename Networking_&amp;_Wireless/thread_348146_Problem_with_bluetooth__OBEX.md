---
title: "Problem with bluetooth / OBEX"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by alingex on 2007-01-28
Hi there,

I've got a bluetooth-problem:
I'm using kbluetoothd with Ubuntu 6.10 to access the services of my Samsung D600, which works very well. I select obex file transfer and all the folders show up.
I can navigate through all folders on my mobile, but: I can't see any files!
Can anybody help me?

(Another small question is: Why does my mobile ask me for permission everytime I open a folder, although the devices are paired?)

Alex

---

### Post by ruibernardo on 2007-05-07
Hi

sorry for this (very) late reply, just saw this post now when I was searching for another thing. I have a Samsung Z300 and it works very well with Ubuntu (not kubuntu), but I think it's not very important.

It seems that the Samsung mobile phones have some security features for bluetooth connections. In your Samsung phone, go to the Settings -> Conection -> Bluetooth -> Devices and highlight your computer, then in Options make it an Authorized Device. Thats for the permission thing in the phone side.

Another thing to change is the definitions of Bluetooth in Ubuntu. There is 2 files you have to change (make a backup copy of those files before changing them and change just those option, don't delete the rest of them): 

 /etc/default/bluetooth:
```
BLUETOOTH_ENABLED=1
HIDD_ENABLED=1
HIDD_OPTIONS="--connect 01:23:45:67:8A:AB [COLOR=Red]-i 01:23:45:67:8A:AB --server[/COLOR]"
SDPTOOL_OPTIONS="add --channel=17 OOP <-- Channel 17 is OOP in my Z300
```/etc/bluetooth/hcid.conf:

```
security user;
pairing multi;
passkey "1234"; <-- That's the default PIN, you should change it.
pin_helper /usr/bin/bluez-pin <-- check what PIN helper you have (depends if it is Gnome or KDE or what you have installed)
lm accept;
```To use your phone as an UMTS modem you have to check what is the channel of the modem in your phone with 

```
sdptool browse 01:23:45:67:8A:AB
```and change the file /etc/bluetooth/rfcomm.conf to use it. To make transfers to my phone I created a "Launcher..." in my Desktop (right click and select Launcher) and put this in the "Command" line (this is for gnome).

```
gnome-obex-send --dest=01:23:45:67:8A:AB
```

Add gnome-obex-server to "Sessions" menu in Gnome (System -> Preferences -> Sessions).

Restart the bluetooth service with

```
sudo /etc/init.d/bluetooth restart
```

Now just drag the files and drop them over the icon and it will send it to the phone, no questions asked :).

My Samsung Z300 works very well with sending and accepting image files, video files, MP3, etc.

For the calendar/agenda/contacts **"sync"** with Evolution, it's only one way here: from the phone to Evolution. This is because my phone uses VCS/ICS 1.0 and Evolution uses version 2.0. But Evolution accepts version 1.0, although it doesn't export as version 1.0 to make them readable by this phone. Check if your phone as version 2.0 to be happy. 

To import those things to Evolution just go to the menu File -> Import -> Import just one file and select the vcs file you sent to Ubuntu (it should be in the Desktop).

I know it's a way too late reply, but I hope it helps anyway :).

[EDIT: added the gnome-obex-server part]

---

