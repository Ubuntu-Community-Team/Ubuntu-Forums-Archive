---
title: "printer networking in ubuntu"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by myharshdesigner on 2007-12-09
i have to computers one is desktop running windowsxp and one is laptop running ubuntu 7.10.


now i want to access my HP printer which is installed on my windows pc.


i have samba install in my ubuntu pc .


so how to to that pl guide me i can able to see my wndows pc and able to access windows drives.

but i cant able to see my printer which is also shared on my windows pc.

you can see in the Attach Files

so pl tell me.

thanks.

---

### Post by myharshdesigner on 2007-12-09
any one can tell me how to solve this problem ?

---

### Post by wjp.reg on 2007-12-09
I don't think you should expect to "see" the windows shared printer as a network share, but it will work anyway if "properly" setup.

---

### Post by myharshdesigner on 2007-12-09
k but as you see in the attachement there is no printer.

acan see my shared perinter on another window pc.

why anh how?

pl help.

---

### Post by wjp.reg on 2007-12-09
> **myharshdesigner said:**
> k but as you see in the attachement there is no printer.

acan see my shared perinter on another window pc.

why anh how?

pl help.

k, but in ubuntu do not expect to see a printer icon.

if you set up the windows printer as a samba share then yu will find it under System | Administration | Printing.  Ubuntu is not windows ;-)

---

### Post by myharshdesigner on 2007-12-09
how to setup printer through samba ?

---

### Post by rm_mn on 2007-12-10
To install a printer that is on a Windows computer connected across a network, click on System>Administration>Printing.  Double click on New Printer.  This should pop up a small window saying that Cups is reading the printer database, then up pops a new window titled Add a Printer with Step one of 3 listed.  Choose Network Printer and select Windows Printer (SMB).   Now you should have several boxes to enter information about the PC that the printer is attached to.  At this point a box popped open with my username and requesting a password.  This confused me for a bit as the Windows PC didn't have a password.  It wanted my password for my Ubuntu box. ](*,)

Give it your password and click connect so it can search the network. Choose the  name of the computer that hosts the printer.  Note that it may take a while for the Windows computer to announce itself on the network as Windows Networking is not the best.  Once Ubuntu has the other computer listed, the available printers will show up in the drop-down box.  Choose the one you want and click next.

Give the printer the name and location you want and you should have a working network printer.

---

### Post by stchman on 2007-12-10
> **myharshdesigner said:**
> i have to computers one is desktop running windowsxp and one is laptop running ubuntu 7.10.


now i want to access my HP printer which is installed on my windows pc.


i have samba install in my ubuntu pc .


so how to to that pl guide me i can able to see my wndows pc and able to access windows drives.

but i cant able to see my printer which is also shared on my windows pc.

you can see in the Attach Files

so pl tell me.

thanks.

My suggestion is to put the printer on your Ubuntu PC and share it on the network.  Ubuntu does a much better job of sharing printers over a network than Windows.  Far easier as well.  TO share your printer with Ubuntu follow this:

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

Since you are running Gutsy then refer to this to enable printer sharing over a network.

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by mcouture on 2007-12-10
> **rm_mn said:**
> To install a printer that is on a Windows computer connected across a network, click on System>Administration>Printing.  Double click on New Printer.  This should pop up a small window saying that Cups is reading the printer database, then up pops a new window titled Add a Printer with Step one of 3 listed.  Choose Network Printer and select Windows Printer (SMB).   Now you should have several boxes to enter information about the PC that the printer is attached to.  At this point a box popped open with my username and requesting a password.  This confused me for a bit as the Windows PC didn't have a password.  It wanted my password for my Ubuntu box. ](*,)

Give it your password and click connect so it can search the network. Choose the  name of the computer that hosts the printer.  Note that it may take a while for the Windows computer to announce itself on the network as Windows Networking is not the best.  Once Ubuntu has the other computer listed, the available printers will show up in the drop-down box.  Choose the one you want and click next.

Give the printer the name and location you want and you should have a working network printer.

I've been fighting this issue for awhile.  I can't see the printer share from the GUI in Ubuntu.  However if I use SMBCLIENT from the command line, I can attach and print to my Windows printer on my Windows box.  
In the GUI, I don't see any printers on my Window box.

---

### Post by rm_mn on 2007-12-10
When I tried it as I was writing the post, it took at least 5 minutes for the Windows PC to show up in the printer utility.  Once there, it showed all the available printers on the Windows PC so I could just choose the one I wanted to install.

In my case I needed to use the printer on the Windows PC because I have my printer port used for my laser printer and the one on the Windows PC is a color inkjet.  I just want it all.;)

---

### Post by Fitzcarraldo on 2007-12-15
This is how I configured Ubuntu 6.06 on a networked laptop to print to a printer connected to a Windows XP PC on the network:

[http://ubuntuforums.org/showthread.php?t=280624](http://ubuntuforums.org/showthread.php?t=280624)

---

