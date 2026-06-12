---
title: "I cant add printer to ubuntu"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by request_another on 2010-05-13
I have a printer hooked up to a windows pc on my network. But i have no idea how to make ubuntu see it. I went to System -- Administration -- Printing. Then a box opens up. For some reason the window title is "Printing - localhost". If i click Server and then New, Printer is grayed out. Also the Add button is grayed out.

---

### Post by request_another on 2010-05-13
ok no worries. It seems the cups service wasnt running.

I ran it with this

sudo /etc/init.d/cups start

And now the buttons arent grayed out :)

---

### Post by walt.smith1960 on 2010-05-13
What brand or model printer?  Some are more Linux friendly than others.  You might take a look at [http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting).  I hope this helps you.

---

### Post by request_another on 2010-05-13
ok im marking this as unsolved because i set up the printer, but nothing prints.

I have an HP Deskjet F380. When i was setting up the printer, there was a driver for the HP Desjet F300 which should be the same. When i send some print jobs ubuntu tells me that they have been sent, but nothing happens.

edit: walt, i checked the link u provided, and it ultimatly led me to the same driver that ubuntu has inbuilt. I tried to install it anyway but it would not detect my printer since i do not have it connected to my ubuntu machine, like i said the printer is connected to my windows pc on the network

---

### Post by request_another on 2010-05-14
can anyone help?

---

### Post by garvinrick4 on 2010-05-14
> **wankingweiner said:**
> can anyone help?

Are you on a Windows Workgroup network?

---

### Post by request_another on 2010-05-14
yes i am. does this matter?

---

### Post by request_another on 2010-05-14
im very certain there's a network problem here because connecting the printer directly to my laptop with usb works fine.

---

### Post by cjazz on 2010-05-14
wankingweiner,

You don't say how you've tried to install your printer, but I assume you've allowed printer sharing on your Windows machine. With some models, it also helps to disable bidirectional printing.

I also assume you've navigated through the printer configuration tool at System>Administration>Printing. Here are the steps that have worked for me as far as installing a printer connected to a Windows host:

1. Select Add.
2. Select Network Printer.
3. Select Windows Printer via SAMBA.

A dialogue should appear with "smb://" followed by a selector box and a "Browse" button. Clicking on Browse should allow you to navigate to your Windows workgroup, where hopefully you can click on the Windows machine to which the printer is connected and find the printer itself. If not, after "smb://" enter the following:

WORKGROUP/COMPUTERNAME/Printername

where "WORKGROUP" is the precise name of your Windows workgroup, "COMPUTERNAME" is the name of the Windows computer, and "Printername" is the exact name of the shared printer in Windows. All this is case sensitive, so pay particular attention to whether the names are upper or lower case.

I apologize if you've already tried all of this, but as I said it has worked for me. Sometimes it pays to experiment a little.

---

### Post by paydaydaddy on 2010-05-14
Which windows version are you using? Do you have a firewall on the windows system? Are you using a firewall GUI on ubuntu (firestarter,etc.)? Have you been to this page:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

A little more info is needed.

---

### Post by request_another on 2010-05-15
@ cjazz, yes this is exactly what i have done so far. I added the printer this way, everything seems to be set up correctly but when i say print a test page, the document was sent for printing but nothing happens.

Im running windows 7, and i've read about bi-directional communication and disabling it, but i am yet to find this setting in windows 7. All talk on the internet is focuses on windows xp and vsita. Windows 7 has a different printing interface.

---

### Post by request_another on 2010-05-15
I found bidirectional support in the settings, i disabled it but it doesnt seem to change anything.

But i did find something interesting. All the test pages that i sent from ubuntu to print actually show up on the print queue on my windows machine.

---

### Post by request_another on 2010-05-15
I have solved the problem!

I found that on my windows machine, there were a few jobs stuck in the queue and the only way to remove them was to restart the printing spool service. Having done that, and with bidirectional support off, it would then print my test pages! I knew this was a windows problem :)

---

### Post by cjazz on 2010-05-15
Congratulations and good work.

---

