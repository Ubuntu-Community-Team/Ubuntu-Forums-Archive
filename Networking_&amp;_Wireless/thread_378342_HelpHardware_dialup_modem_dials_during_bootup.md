---
title: "Help:Hardware dialup modem dials during bootup"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by izak on 2007-03-07
Hi all
I've managed to track down an external hardware serial modem. I can connect using System>Administration>Networking and gnome-ppp (current preferred method) like the DailUpModemHowTo recommends. 

However, after configuring gnome-ppp, when I switch on the modem it automatically dials and connects to the internet! Two scenarios:
a) Switch on modem and then boot PC. The modem starts dialing during the bootup process.
b) Boot and then switch on modem. The modem immediately starts dialing.

It has to be ubuntu telling it to dial, how else would it know my connection details? However the gnome-ppp connected icon doesn't appear on the taskbar, so I have to switch the modem off again to disconnect. When I switch it on a second time, it behaves as expected (doesn't dial) and allowes me to use gnome-ppp to connect, monitor and disconnect.

Its not catastrophic, but its irritating. Any ideas on solving the problem?

Thanks!

---

### Post by NJC on 2007-03-20
Under System>Administration>Networking isn't there an option to reconnect to the 'net when a connection is missing or broken?

Upon re-reading your post, it also happens on boot which is the same problem I am having. Your modem probably dials after the "configuring network services.." section of boot.

Anyone have insight on this? I assume it's hiding in a boot script somewhere.

EDIT: This may be the problem:

The Networking section of System => Administration will let you set up the ppp connection in a graphical interface. You have to know your device name, ISP phone number, username and password to set it up. You can also use the Gnome Modem Monitor and Network Monitor panel applets if you want to stop, start and monitor modem connections without opening the Networking GUI every time. **Some people have had a problem with the modem dialing during bootup. This may be related to setting the modem as default route to the internet on the Options tab of Interface properties. **

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6)

---

### Post by d4ndy on 2007-04-29
I just made a clean install of Xubuntu 7.04 and had this problem (modem starting on boot). I had used the Applications?System?Network route just to get online long enough to download gnome-ppp, but then I found the "Modem Connection" in System didn't want to relinquish power.  I tried changing a few of the settings mentioned above, like the reconnect setting (and let me tell you it's a treat trying to debug a modem connection while referencing searches online, since nearly every change means you lose the connection and have to start over), but soon enough I found that unchecking "Modem Connection" on the System main page disabled it (how 'bout that?) and put gnome-ppp back in the driver's seat by default.
(I've also had problems with the terminal startup logging me out of X , the eternal "difference between boot sector & its backup" controversy, quodlibet installing incompletely and brokenly through synaptic, but perfectly through aptitude, and I few others. But then, what linux installation would be complete without a little command line action?):)

---

### Post by d4ndy on 2007-04-29
Oops -- make that unchecking "Modem Connection" on the System / *Network* main page.

---

