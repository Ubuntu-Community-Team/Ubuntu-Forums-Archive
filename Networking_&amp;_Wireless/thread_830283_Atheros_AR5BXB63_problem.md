---
title: "Atheros AR5BXB63 problem"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by Nidding on 2008-06-15
I have just made a fresh install of hardy from a gutsy studio install. At the same time as I did this, my wired network connection broke down and I'm left with a wireless connection.
Can anyone tell me how to get the wireless card to work, without a network connection (I have a vista machine, so I can download, just not on the ubuntu machine)

---

### Post by Nidding on 2008-06-16
I found this in a thread in the archive

> **surfduke2001 said:**
> I have installed Ubuntu test of 8.04 on My new laptop, (Dual Boot with the evil Vista, (LOL)). The only trouble was the wireless connect. 

I have done the following and it works now, (Make sure You have a hard line net connection) :

1. Install the ndisgtk program from the package Synaptic Package Manager
2. Windows XP atheros driver from acer.com.cn, pick Wireless Atheros driver.
3. Make a folder in documents file, (I named it Wireless driver).
4. Move the downloaded .zip file from desktop to the new wireless folder.
5. Right click on the .zip file, (and choose extra here).
6. Go to System>Administration>Windows Wirless Drivers, (NDISWRAPPER will open now, (after password is given)).
7. Choose Install Driver.
8. Goto location line, click on the right folder tab and browse to:
Document>Wireless driver>Wireless_Atheros_XP32_XP64_WHQL_(5.3.0.45_logo)>XP32_XP64_WHQL_5-3-0-45_(Negative-Pole)70510>net5211.inf
9. Choose to intall.
10. The driver should now appear in the list on the left.
11. Select the driver, (Left click to highlight), and choose the configure network button, (This will take a few moments.
12. Reboot, Choose the network manager on the tool bar.
13. Select a wireless network, (Surf........)

Have a great day,

Carl

But is there a way to do it without using the package manager and downloading the packages on another comp?

---

### Post by falcon61102 on 2008-08-31
Oops

---

