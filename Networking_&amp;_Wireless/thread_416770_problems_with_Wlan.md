---
title: "problems with Wlan"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Bart Ellebaut on 2007-04-21
hey,

I've got some problems with my Wlan.
I've configured my wlan, it says: active, but no connectoin.
I've downloaded my driver (for windows), + the new ndiswrapper 1.42
Now I've tried to install in thx to an other post on this forum, there it says: install headers, but I can't find them

then I tried to install indiswrapper, but when I type cd /home/(my username), I get: no such file or directory

what do I have to do?

thx

---

### Post by Kobalt on 2007-04-21
The easiest way for you to install your card is to open Synaptic package manager in System > Admin. menu. Then search for a package named *ndisgtk*. Install it. 
After that, go to System > Admin. > Windows Wireless Drivers : you will access ndiswrapper in a graphical mode, from there you'll be able to install the drivers for your card really easily.
Then you can use Network-Manager to access your wireless network pretty easily.

---

### Post by Bart Ellebaut on 2007-04-22
I have tried this, but he can't find ndisgtk (still got ubuntu 6.06)
nowhere I can find windows driver... but I've already downloaded them for linux!!
I have downloaded ndiswrapper 1.42, so what should I do?

---

### Post by Bart Ellebaut on 2007-04-23
OK, I've tried this. I've Installed ndisgtk,  and I've downloaded the driver for windows.
I went to the wireless windows driver.
There it says I have to select a inf., now, I've got 3 of them, so I have tried all 3 off them, and pressed instal, but it does nothing.
Nothing appears, and no new driver is added to the list.
what am I doing wrong??

thx
Bart

---

### Post by Bart Ellebaut on 2007-04-26
nobody has any idea??

---

