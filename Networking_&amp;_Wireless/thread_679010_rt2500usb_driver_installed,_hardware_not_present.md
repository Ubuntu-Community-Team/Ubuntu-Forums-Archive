---
title: "rt2500usb: driver installed, hardware not present"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by Game_boy on 2008-01-26
I can't connect to the internet by wireless (I have a working eth0 connection). I am using a Belkin F5D7050 USB adapter containing a Ralink rt2500usb chipsetfor which I am using the default Gutsy driver. It randomly disconnects itself every five minutes.

---

### Post by Game_boy on 2008-01-27
Anyone?

---

### Post by rustybronco on 2008-01-27
what version of the f5d7050 do you have?

---

### Post by kevdog on 2008-01-27
Hmm, can you post

lsmod

(Filter the output to include an rt or ndiswrapper output.  I think this command would be:
lsmod | egrep ('rt|ndis")

---

### Post by Game_boy on 2008-01-27
I disabled ndiswrapper and the Gutsy built-in driver works, but randomly disconnects every five minutes.

---

### Post by kevdog on 2008-01-27
Id suggest either one of two approaches at this point with #1 being relatively easier:

#1 - Use the serial monkey rt2500 drivers
#2 - Upgrade your kernel to hardys developmental kernel and use the rt2x00 driver.

Are you on a 32bit Ubuntu install?

---

