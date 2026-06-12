---
title: "[SOLVED] find windows host on wireless network"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by kaushd on 2008-03-19
hi,

i'm trying to share folders between a windows & linux box via wifi, but having trouble at the initial stages just finding the client over wireless.

both boxes connect to the net using the same wireless router, connecting to the net is fine, but I can't find each host of the network?

the ubuntu box ip address is 192.168.1.37 & the windows box is 192.168.1.36 (both dhcp) I've tried pinging linux -> windows & windows -> linux, but no joy.

can someone point me in the right direction? I've searched and found tutorials on samba etc, but my need seems to be much more basic than that (just can't find the each other in the first place).

pls help!

---

### Post by BDNiner on 2008-03-19
If you go to "places" there are two options. "connect to server" and "network". "network" will let you browse to any computers on the same subnet. "connect to server" will let you connect to the windows share directly. you just have to select windows share from the drop down list. Also if you right click on the share and select "connect to this server" it will mount the share to desktop.

---

### Post by Eiríkr on 2008-03-19
Ping-wise, you've presumably already tried pinging by IP?  If so, can you at least ping your router from each machine?  

Cheers,

Eiríkr

---

### Post by neerajadsul on 2008-03-19
In windows you need to check out firewall settings. Also if you have any antivirus running then also could be a problem. Try to turn off antivirus + Windows Firewall for couple of minutes and then try again.
And as Eiríkr has said, try pinging Router from both machines first.

---

### Post by kaushd on 2008-03-19
result!

thanks for the suggestions. it was the firewall on the windows box that was causing the issue (zonealarm). i added my ubuntu box's ip address to zonealarm's trusted zone and everything started working straight away.

 i can access all folders on my windows box. now to start sharing my linux folders too.

many thanks for everyone's help!

---

### Post by Eiríkr on 2008-03-19
Glad to hear it's working!  :)  And since your issue is fixed, please also remember to mark this thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :D

Thank you,

Eiríkr

---

