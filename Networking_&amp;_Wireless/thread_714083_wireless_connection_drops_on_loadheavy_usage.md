---
title: "wireless connection drops on load/heavy usage"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by gulac on 2008-03-03
Hello everybody,

I have a problem with my Ubuntu installation and after doing some research I have come to you for help. 

Here is a quick system description:

- Via Sp13000 Mini-Itx motherboard
- Dlink WUA-2340 USB wireless
- Ubuntu 7.10
- ndiswrapper 1.52 which I compiled
- the latest Dlink Windows driver from the website
- WPA personal encryption
- Ubuntu's network manager

My problem is that my wireless connection drops under load. I can browse to simple websites okay but it keeps disconnecting if I try transferring big files. This is a problem for me because, I've set up an ftp server and use my box as a movie player with Geexbox (dual boot). I would like to transfer my files to the box which is plugged in the TV but the connection is not stable enough for 700mb to 1GB files. To make things worst, I have to reboot the box when this happens because the adapter isn't recognized anymore.

The card works fine in Windows and transferring big files works fine with eth0. 

Thanks in advance for your help !

---

### Post by gulac on 2008-03-04
I have better stability with my connection since I installed WICD. Now, could there be something wrong with the FTP server I'm using ? (vsftpd)

---

