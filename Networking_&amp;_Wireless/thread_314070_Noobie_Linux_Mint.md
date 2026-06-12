---
title: "Noobie Linux Mint"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by mandalay559 on 2006-12-07
Hello, I am new to the world of Linux and this forum, I hope I posted correctly.  I installed Linux Mint recently on my second drive.

I cant get any internet.  I have a wireless Zyxel:confused:  g-202 usb adapter that I use in Windows.

I have no clue how to make this work in the Ubuntu Linux Mint.
I googled everywhere and am very lost.  I am not experienced in command line stuff.  I guess I just need step by step instructions if possible.  When i go to the device manager area it shows the zyxel adapter, its just that its not installed or must need a driver??

I really want to try Ubuntu out but need to get this adapter to work.  Please help.

---

### Post by mandalay559 on 2006-12-07
hello can anyone help me out with getting my zyxel G-202 wireless adapter working?  I dont know how to load the driver or find the correct one.

What is Edgy and will it help me or Wine?

Thanks

---

### Post by kasulstyls on 2006-12-07
not all cards are supported under linux.  

check this list to see if your card is supported with below link.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by FrodoB on 2006-12-07
Publish the output of:

lspci -v

---

### Post by gjtoth on 2006-12-07
> **mandalay559 said:**
> hello can anyone help me out with getting my zyxel G-202 wireless adapter working?  I dont know how to load the driver or find the correct one.

What is Edgy and will it help me or Wine?

Thanks

Edgy is the latest version of Ubuntu (except for the upcoming Feisty Fawn).  Wine is a WINdows Emulator and it won't be of any use to you right now.  Unfortunately, I don't have any experience with WiFi stuff.  Sooooo, looks like you're going to have to do some searching on these forums or be patient and wait for those that are more knowledgeable to come up with a solution.

---

### Post by FrodoB on 2006-12-07
Ubuntu 6.10 code named Edgy Eft is the latest version of the Ubuntu distribution of GNU/Linux.

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Wine is an Open Source implementation of the __Windows API on top of __ X and Unix/Linux/BSD:

[http://www.winehq.com/](http://www.winehq.com/)

---

