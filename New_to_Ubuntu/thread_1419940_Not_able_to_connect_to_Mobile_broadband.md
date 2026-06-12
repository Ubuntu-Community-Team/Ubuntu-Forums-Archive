---
title: "Not able to connect to Mobile broadband"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by praveen_pa on 2010-03-02
I have installed Ubuntu 9.10 and connecting net thru wvdial.but i'm not able to connect it thru "network manager".When try to connect it thru network manager displays "Network disconnected"

Please help to connect net thru "Network Manager"

Thanks
Praveen

---

### Post by Arijit_Kundu on 2010-03-02
add and set up your connection first. right click on the network icon in the system tray, select 'edit connections'. There is a tab 'mobile broadband'. clicking 'add' will take you through a process.

---

### Post by iponeverything on 2010-03-02
maybe it would help if you told us what kind of modem are using?

Does an icon for the device show up on the desktop?

if so, right click on it, go to eject and then check network manager.

---

### Post by praveen_pa on 2010-03-05
Thanks for the reply.I'm using BSNL 3G CDMA2000 IX EVDO data card. I don't find any icon on the desktop but able to see it using "lsusb".

$ lsusb
Bus 002 Device 002: ID 19d2:fffe ONDA Communication S.p.A. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I have added the connection to the network manager using "edit connections" and it is available under MObile broadband.But when clicked, it displays "Network disconnected".

Please let me know if any other details required.Again,Thank you for the help.

----------------------------------
Praveen

---

