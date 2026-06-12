---
title: "Sambe file tranfers error"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by rubrboots on 2007-05-19
I have samba installed and it works well until I try to transfer files. I download video files with a fiesty ubuntu machine, then I transfer them to a windows machine that acts as a PVR. When I transfer files from the unbuntu box to the windows box I get a "Error time out reached" about halfway though the transfer. I have never had this problem with transfers between windows machines. Does anyone know how to fix this, or where to start looking?

---

### Post by tormentum on 2007-05-20
How big is the file you are trying to transfer?  Is it larger than 4GB?  Do you get the same error when transfering smaller files?  Say, 10Mb?

---

### Post by rubrboots on 2007-05-20
the files I am transferring are usually 500-700 Mb. I have not really tried smaller files, however some files will complete but most will not. As well when they do transfer it takes about twice as long as it would for a windows to windows transfer.

---

### Post by tormentum on 2007-05-20
hrm, in that case I'm not too sure.  The only time i've had probs like that is when I've had a flakey network card.  Whenever I'd put the card under strain, it'd start to loose packets, hence the errors while transfering files.  That was Windows to Windows though.  Not sure if it'll do you any good but you could try a) changing the cable/router/switch you're using and b) test transfering files with another program; eg: http transfers or try setting up a large packet ping and see if you start to loose packets after a little while.

ping 192.168.0.1 -s 20000 is a good ping packet size.  Just a thought.

Do you have a spare PCI network card you can place in the back of the machine and test out?

---

### Post by rubrboots on 2007-05-21
ok, I swapped the NIC and the problem persists. Strange thing though, instead this time I browsed the file to be copied from the windows machine, and copied from the ubuntu machine to the windows machine in this manner.  The file transferred with no errors and quickly just like before when it was windows to windows.  Whats going on? This method can work but its very inconvenient since I have to remote desktop the windows box to do this. I would much rather manage the files from the ubuntu box.  Any ideas??

---

