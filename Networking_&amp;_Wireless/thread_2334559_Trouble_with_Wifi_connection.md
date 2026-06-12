---
title: "Trouble with Wifi connection"
date: 2016-08-20
forum: Networking &amp; Wireless
---

### Post by lusbyclark2 on 2016-08-20
Some years ago I upgraded the Ubuntu OS on my PC from 12.04.4 to 14.04.3 and was very pleased how well things have worked.  I recently upgraded to 16.04.1 and found that everything continued to work well.  Then yesterday the ATT U-Verse "gateway" box in my house failed and their technician came out to replace it.  It came with a different 12-digit passcode than was installed in the failed gateway box.  So I asked him to change the passcode in the new box to the one in the old box.  My wife's Windows 7 PC got back on the internet right away, but I had to go around and reinstall the passcode in her Galaxy tablet, our Epson printer and a Kindle Fire.  I am fairly certain all of my grandsons will be reinstalling the passcode in their smart phones when they come around for another visit.  However, I cannot get my Linux PC to work with this new ATT gateway box.  I right-click on the "transmitting" Icon in the upper-right hand corner of the display, after which a dialog box comes up with the proper network name in one of its text boxes.  I found the old passcode still stored in the only text box labeled password.  But it just won't connect.   What am I doing wrong?

---

### Post by Keith_Helms on 2016-08-23
I'm not following.  If you had the technician set the passcode in the new box to be the same as in the old box, why did you have to reinstall the passcode in a printer and 2 tablets?  Did the network name change?

---

### Post by lusbyclark2 on 2016-08-27
My answer to the one reply is: I do not understand that myself.  This computer stuff is frequently a complete mystery to me.

---

### Post by chili555 on 2016-08-27
Network Manager keeps track of access points and passwords and, included in the data it keeps is the device's MAC address. When you got a new gateway, it has a different MAC address. It may look the same, it may be named the same, but its fingerprint is different. For security reasons, your computer will not connect automagically to an imposter. Many a hack has taken place at the coffee shop where the hacker knows the network's name and password and spoofs it to get you to connect to them and not the coffee shop's wifi, so that they can steal your bank log-in, etc.

Let's try to erase the details from Network Manager, reboot and see if you connect. Please open a terminal and do:```
sudo rm /etc/NetworkManager/system-connections/*
```CAUTION: the command 'rm' for remove is powerful, permanent and unforgiving. Type carefully and proofread twice before you press Enter.

Reboot. Your computer should tell you that networks are avaiable, ask for a password and connect. Post back if not.

---

