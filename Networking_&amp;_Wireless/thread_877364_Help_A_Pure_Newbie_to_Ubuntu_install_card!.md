---
title: "Help A Pure Newbie to Ubuntu install card!"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by ballerali on 2008-08-01
So I am extremely fed up with Windows
and I decided to install Ubuntu.

Problem is, I cant get my WG111T Netgear USB card to work so I can access the internet!

I've read some other instructions but there too confusing..ndwiskrapper?? 

So I would really appreciate someone explaining to me how to get it to work using baby steps and language... thanks guys!

---

### Post by mb_webguy on 2008-08-02
The hardest part of using ndiswrapper is finding the Windows driver.  Once you have it, install ndiswrapper and its GUI by typing "sudo apt-get install ndisgtk" in the terminal.  Now just go to System->Windows Wireless Drivers, click "Install New Driver", and select the .inf file.  Then restart networking by restarting your computer (or possibly typing "sudo /etc/init.d/networking restart" in the terminal). Now you should be able to right-click the Network Manager applet to view a list of available wireless networks.

---

### Post by jeremy1138 on 2008-08-02
The network card isn't listed in the restricted drivers manager?

---

### Post by ballerali on 2008-08-02
Sorry I have no idea what Ndiskwrapper is.

So I have the driver windows file on the Ubuntu desktop...how do I install it nothing happens when I double click it.

---

### Post by Sealbhach on 2008-08-02
> **ballerali said:**
> Sorry I have no idea what Ndiskwrapper is.


Ndiswrapper is a Linux module which allows Ubuntu to use the Windows driver for wireless cards (in most cases).

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

> **ballerali said:**
> 
So I have the driver windows file on the Ubuntu desktop...how do I install it nothing happens when I double click it.

That link there should help you get the windows driver working in Linux.

Any problems just holler but it should work OK for you.


.

---

