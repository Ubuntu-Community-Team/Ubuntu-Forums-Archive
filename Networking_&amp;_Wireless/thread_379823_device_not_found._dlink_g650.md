---
title: "device not found. dlink g650"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by davekenny on 2007-03-08
help...
My wifi card stopped working..
background
runs fine under 2.6.17.10 but not 2.6.17.11, but until 2 days ago it worked fine under 2.6.17.11
the machine is setup as a dual boot. it works in windows XP
it seemed to quit after trying to run vmware converter software to convert the XP to 
vmware server virtual machine.

I'm not use ndiswrapper.
the wireless network is open.
the card doesn't show in the network manager. in the device manager it finds the card.

what should I check? I have only been using Ubuntu since Jan this year. so its still pretty new to me.


-dave

---

### Post by davekenny on 2007-03-09
I got it working finally.

I download the madwifi drivers, rebuilt them and reinstalled them.
the readme and intall directions weren't clear enough for me. I eventually found
the howto for the madwifi and followed the directions.

the key was the 
make clean
make
make install

then everything worked!!! :):)

dave

---

