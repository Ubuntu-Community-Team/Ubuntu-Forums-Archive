---
title: "General Network Help For a Newbie"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Aszat on 2008-09-25
Can some please help me set up my home network. I am an average computer user. I have just installed Ubuntu HH dual boot with xp pro and i can get on the internet but i need to share my printer and at least 1 folder with a Laptop running WinXP thats wireless.

---

### Post by superprash2003 on 2008-09-25
for this you require samba..read this
1) samba install - [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)
2)share printer - [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by Aszat on 2008-09-25
I followed the first procedure but my xp pc cant see the liux same for printing

---

### Post by superprash2003 on 2008-09-26
firstly, ensure that the two pcs are able to ping each other, have you configured samba properly?

---

### Post by Aszat on 2008-09-26
They can ping each other. I Assume i have set up samba correctly. I have followed your guides.

---

### Post by cariboo on 2008-09-26
Check to make sure both computers are in the same workgroup, some XP  installations default to MShome and Ubuntu defaults to workgroup. If you are familiar with XP it should be easier for you to change the workgroup in xp.

Jim

---

### Post by superprash2003 on 2008-09-28
are you able to share files via samba ?? go to system->admin->Printing and under policies ensure that "shared" is ticked..

---

### Post by Aszat on 2008-09-28
YEs printer shareing is enabled

---

### Post by superprash2003 on 2008-09-29
when you are trying to connect to the ubuntu printer from xp.. after you click on Add printer, then you should find a place wherein you can manually enter the link of the printer.. there type in \\x.x.x.x\officejet_6200_series_... the last part is not visible.. basically x.x.x.x is the ubuntu machine's ip address on the network.. you can find it by typing ifconfig in the terminal.. and the officejet_6200_series is your printername

---

